```javascript
/**
 * 更改为模块化
 * 该方法只支持 ASCII 码支持的字符, 其它字符可能会出现异常
 * 三个基础方法, 只有一个参数为要加密的字符串
 *     roc.sha1.hex(string) 摘要算法后 十六进制 输出
 *     roc.sha1.b64(string) 摘要算法后 base64编码 输出
 *     roc.sha1.str(string) 摘要算法后转化为 字符串 输出
 * 三个高级方法, 第一个参数是秘钥, 第二个参数是要加密的字符串
 *     roc.sha1.hamcHex(key, data) 摘要加密算法后 十六进制 输出
 *     roc.sha1.hamcB64(key, data) 摘要加密算法后 base64编码 输出
 *     roc.sha1.hamcStr(key, data) 摘要机密算法后 字符串 输出
 * 三个可配置参数
 *     hexcase: 十六进制输出格式, 0 小写, 1 大写
 *     b64pad:  base64 缺省字符, "=" 严格遵守 RFC
 *     chrsz:   每个输入字符的位, 8-ASCII；16-Unicode
 */
const roc = {};
(function(roc, hexcase, b64pad, chrsz) {
	roc.sha1 = {};
	roc.sha1.hex = function(s) {
		return binb2hex(core_sha1(str2binb(s), s.length * chrsz))
	};
	roc.sha1.b64 = function(s) {
		return binb2b64(core_sha1(str2binb(s), s.length * chrsz))
	};
	roc.sha1.str = function(s) {
		return binb2str(core_sha1(str2binb(s), s.length * chrsz))
	};
	roc.sha1.hamcHex = function(key, data) {
		return binb2hex(core_hmac_sha1(key, data))
	};
	roc.sha1.hamcB64 = function(key, data) {
		return binb2b64(core_hmac_sha1(key, data))
	};
	roc.sha1.hamcStr = function(key, data) {
		return binb2str(core_hmac_sha1(key, data))
	};

	function sha1_vm_test() {
		return hex_sha1("abc") == "a9993e364706816aba3e25717850c26c9cd0d89d"
	}

	function core_sha1(x, len) {
		x[len >> 5] |= 128 << (24 - len % 32);
		x[((len + 64 >> 9) << 4) + 15] = len;
		var w = Array(80),
			a = 1732584193;
		var b = -271733879,
			c = -1732584194;
		var d = 271733878,
			e = -1009589776;
		for (var i = 0; i < x.length; i += 16) {
			var olda = a,
				oldb = b,
				oldc = c,
				oldd = d,
				olde = e;
			for (var j = 0; j < 80; j++) {
				if (j < 16) {
					w[j] = x[i + j]
				} else {
					w[j] = rol(w[j - 3] ^ w[j - 8] ^ w[j - 14] ^ w[j - 16], 1)
				}
				var p1 = safe_add(rol(a, 5), sha1_ft(j, b, c, d));
				var p2 = safe_add(safe_add(e, w[j]), sha1_kt(j));
				var t = safe_add(p1, p2);
				e = d;
				d = c;
				c = rol(b, 30);
				b = a;
				a = t
			}
			a = safe_add(a, olda);
			b = safe_add(b, oldb);
			c = safe_add(c, oldc);
			d = safe_add(d, oldd);
			e = safe_add(e, olde)
		}
		return Array(a, b, c, d, e)
	}

	function sha1_ft(t, b, c, d) {
		if (t < 20) {
			return (b & c) | ((~b) & d)
		}
		if (t < 40) {
			return b ^ c ^ d
		}
		if (t < 60) {
			return (b & c) | (b & d) | (c & d)
		}
		return b ^ c ^ d
	}

	function sha1_kt(t) {
		return (t < 20) ? 1518500249 : (t < 40) ? 1859775393 : (t < 60) ? -1894007588 : -899497514
	}

	function core_hmac_sha1(key, data) {
		var bkey = str2binb(key);
		if (bkey.length > 16) {
			bkey = core_sha1(bkey, key.length * chrsz)
		}
		var ipad = Array(16),
			opad = Array(16);
		for (var i = 0; i < 16; i++) {
			ipad[i] = bkey[i] ^ 909522486;
			opad[i] = bkey[i] ^ 1549556828
		}
		var hash = core_sha1(ipad.concat(str2binb(data)), 512 + data.length * chrsz);
		return core_sha1(opad.concat(hash), 512 + 160)
	}

	function safe_add(x, y) {
		var lsw = (x & 65535) + (y & 65535);
		var msw = (x >> 16) + (y >> 16) + (lsw >> 16);
		return (msw << 16) | (lsw & 65535)
	}

	function rol(num, cnt) {
		return (num << cnt) | (num >>> (32 - cnt))
	}

	function str2binb(str) {
		var bin = Array();
		var mask = (1 << chrsz) - 1;
		for (var i = 0; i < str.length * chrsz; i += chrsz) {
			bin[i >> 5] |= (str.charCodeAt(i / chrsz) & mask) << (32 - chrsz - i % 32)
		}
		return bin
	}

	function binb2str(bin) {
		var str = "";
		var mask = (1 << chrsz) - 1;
		for (var i = 0; i < bin.length * 32; i += chrsz) {
			str += String.fromCharCode((bin[i >> 5] >>> (32 - chrsz - i % 32)) & mask)
		}
		return str
	}

	function binb2hex(binarray) {
		var hex_tab = hexcase ? "0123456789ABCDEF" : "0123456789abcdef";
		var str = "";
		for (var i = 0; i < binarray.length * 4; i++) {
			str += hex_tab.charAt((binarray[i >> 2] >> ((3 - i % 4) * 8 + 4)) & 15) + hex_tab.charAt((binarray[i >>
				2] >> ((3 - i % 4) * 8)) & 15)
		}
		return str
	}

	function binb2b64(binarray) {
		var tab = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/";
		var str = "";
		for (var i = 0; i < binarray.length * 4; i += 3) {
			var triplet = (((binarray[i >> 2] >> 8 * (3 - i % 4)) & 255) << 16) | (((binarray[i + 1 >> 2] >> 8 * (
				3 - (i + 1) % 4)) & 255) << 8) | ((binarray[i + 2 >> 2] >> 8 * (3 - (i + 2) % 4)) & 255);
			for (var j = 0; j < 4; j++) {
				if (i * 8 + j * 6 > binarray.length * 32) {
					str += b64pad
				} else {
					str += tab.charAt((triplet >> 6 * (3 - j)) & 63)
				}
			}
		}
		return str
	}
})(roc, 0, "=", 8);
export default roc;

```
