.prettierrc.json配置详解

```javascript
const prettierrc = {
  $schema: "http://json-schema.org/draft-04/schema#",
  definitions: {
    optionsDefinition: {
      type: "object",
      properties: {
        arrowParens: {
          description: "在箭头函数单参数周围包括括号。",
          default: "always",
          oneOf: [
            {
              enum: ["always"],
              description: "始终包括括号。示例: `(x) => x`",
            },
            {
              enum: ["avoid"],
              description: "尽可能省略括号。示例：`x => x`",
            },
          ],
        },
        bracketSameLine: {
          description:
            "将>的开始标记放在最后一行，而不是放在新一行。",
          default: false,
          type: "boolean",
        },
        bracketSpacing: {
          description: "在括号之间打印空格。",
          default: true,
          type: "boolean",
        },
        cursorOffset: {
          description:
            "打印（到stderr），在格式化后，给定位置的光标将移动到该位置。此选项不能与--range start和--range end一起使用。",
          default: -1,
          type: "integer",
        },
        editorconfig: {
          description:
            "是否分析项目中的.editorconfig文件并将其财产转换为相应的Prettier配置。此配置将被.fileterrc等覆盖。",
          default: false,
          type: "boolean",
        },
        embeddedLanguageFormatting: {
          description:
            "控制Prettier如何格式化嵌入文件中的引用代码。",
          default: "auto",
          oneOf: [
            {
              enum: ["auto"],
              description:
                "如果Prettier能够自动识别嵌入代码，则设置嵌入代码的格式。",
            },
            {
              enum: ["off"],
              description: "永远不要自动格式化嵌入的代码。",
            },
          ],
        },
        endOfLine: {
          description: "要应用的行尾字符。",
          default: "lf",
          oneOf: [
            {
              enum: ["lf"],
              description:
                "仅限换行符（\n），在Linux和macOS上以及git repos内部常见",
            },
            {
              enum: ["crlf"],
              description:
                "回车+换行字符（\r\n），在Windows上常见",
            },
            {
              enum: ["cr"],
              description:
                "仅限回车符（\r），很少使用",
            },
            {
              enum: ["auto"],
              description:
                "维护现有\n（一个文件中的混合值通过查看第一行之后使用的内容进行标准化）",
            },
          ],
        },
        filepath: {
          description:
            "指定输入文件路径。这将用于进行解析器推理。",
          type: "string",
        },
        htmlWhitespaceSensitivity: {
          description: "如何处理HTML中的空白。",
          default: "css",
          oneOf: [
            {
              enum: ["css"],
              description: "尊重CSS显示属性的默认值。",
            },
            {
              enum: ["strict"],
              description: "空白被认为是敏感的。",
            },
            {
              enum: ["ignore"],
              description: "空白被认为是不敏感的。",
            },
          ],
        },
        insertPragma: {
          description:
            "在文件的第一个文档块注释中插入@format pragma。",
          default: false,
          type: "boolean",
        },
        jsxSingleQuote: {
          description: "在JSX中使用单引号。",
          default: false,
          type: "boolean",
        },
        parser: {
          description: "要使用的解析器。",
          anyOf: [
            {
              enum: ["flow"],
              description: "Flow",
            },
            {
              enum: ["babel"],
              description: "JavaScript",
            },
            {
              enum: ["babel-flow"],
              description: "Flow",
            },
            {
              enum: ["babel-ts"],
              description: "TypeScript",
            },
            {
              enum: ["typescript"],
              description: "TypeScript",
            },
            {
              enum: ["acorn"],
              description: "JavaScript",
            },
            {
              enum: ["espree"],
              description: "JavaScript",
            },
            {
              enum: ["meriyah"],
              description: "JavaScript",
            },
            {
              enum: ["css"],
              description: "CSS",
            },
            {
              enum: ["less"],
              description: "Less",
            },
            {
              enum: ["scss"],
              description: "SCSS",
            },
            {
              enum: ["json"],
              description: "JSON",
            },
            {
              enum: ["json5"],
              description: "JSON5",
            },
            {
              enum: ["json-stringify"],
              description: "JSON.stringify",
            },
            {
              enum: ["graphql"],
              description: "GraphQL",
            },
            {
              enum: ["markdown"],
              description: "Markdown",
            },
            {
              enum: ["mdx"],
              description: "MDX",
            },
            {
              enum: ["vue"],
              description: "Vue",
            },
            {
              enum: ["yaml"],
              description: "YAML",
            },
            {
              enum: ["glimmer"],
              description: "Ember / Handlebars",
            },
            {
              enum: ["html"],
              description: "HTML",
            },
            {
              enum: ["angular"],
              description: "Angular",
            },
            {
              enum: ["lwc"],
              description: "Lightning Web Components",
            },
            {
              type: "string",
              description: "Custom parser",
            },
          ],
        },
        pluginSearchDirs: {
          description:
            "在node_modules子目录中包含更漂亮插件的自定义目录。Overrides在相对于Prettier的位置搜索插件时的默认行为。可接受多个值。",
          default: [],
          oneOf: [
            {
              type: "array",
              items: {
                type: "string",
              },
            },
            {
              enum: [false],
              description: "禁用插件自动加载。",
            },
          ],
        },
        plugins: {
          description:
            "添加一个插件。多个插件可以作为单独的`--plugin`传递。",
          default: [],
          type: "array",
          items: {
            type: "string",
          },
        },
        printWidth: {
          description: "一行超过设置值长度将尝试进行换行。",
          default: 80,
          type: "integer",
        },
        proseWrap: {
          description: "如何包装散文。",
          default: "preserve",
          oneOf: [
            {
              enum: ["always"],
              description: "如果超过打印宽度，请换行。",
            },
            {
              enum: ["never"],
              description: "不要把散文包装起来。",
            },
            {
              enum: ["preserve"],
              description: "按原样包装散文。",
            },
          ],
        },
        quoteProps: {
          description: "当对象中的属性被引用时更改。",
          default: "as-needed",
          oneOf: [
            {
              enum: ["as-needed"],
              description:
                "只在需要的地方在对象属性周围添加引号。",
            },
            {
              enum: ["consistent"],
              description:
                "如果对象中至少有一个属性需要引用，则需要引用所有属性。",
            },
            {
              enum: ["preserve"],
              description:
                "尊重对象属性中引号的输入使用。",
            },
          ],
        },
        rangeEnd: {
          description:
            "格式化以给定字符偏移量(不包含)结束的代码。范围将向前扩展到所选语句的末尾。此选项不能与--cursor-offset一起使用。",
          default: null,
          type: "integer",
        },
        rangeStart: {
          description:
            "从给定字符偏移量开始格式化代码。范围将向后扩展到包含所选语句的第一行的开头。此选项不能与--cursor-offset一起使用。",
          default: 0,
          type: "integer",
        },
        requirePragma: {
          description:
            "要求在文件的第一个文档块注释中出现'@pretty '或'@format'，以便对其进行格式化。",
          default: false,
          type: "boolean",
        },
        semi: {
          description: "添加分号。",
          default: true,
          type: "boolean",
        },
        singleAttributePerLine: {
          description:
            "在HTML、Vue和JSX中强制每行使用单个属性。",
          default: false,
          type: "boolean",
        },
        singleQuote: {
          description: "用单引号代替双引号。",
          default: false,
          type: "boolean",
        },
        tabWidth: {
          description: "每个缩进级别的空格数。",
          default: 2,
          type: "integer",
        },
        trailingComma: {
          description:
            "多行时尽可能打印尾随逗号。",
          default: "es5",
          oneOf: [
            {
              enum: ["es5"],
              description:
                "尾随逗号在ES5中有效(对象、数组等)",
            },
            {
              enum: ["none"],
              description: "后面没有逗号。",
            },
            {
              enum: ["all"],
              description:
                "尽可能以逗号结尾(包括函数参数)。",
            },
          ],
        },
        useTabs: {
          description: "用制表符而不是空格缩进。",
          default: false,
          type: "boolean",
        },
        vueIndentScriptAndStyle: {
          description: "缩进Vue文件中的脚本和样式标记。",
          default: false,
          type: "boolean",
        },
      },
    },
    overridesDefinition: {
      type: "object",
      properties: {
        overrides: {
          type: "array",
          description:
            "提供一个模式列表来覆盖prettier的配置。",
          items: {
            type: "object",
            required: ["files"],
            properties: {
              files: {
                description: "在重写中包含这些文件。",
                oneOf: [
                  {
                    type: "string",
                  },
                  {
                    type: "array",
                    items: {
                      type: "string",
                    },
                  },
                ],
              },
              excludeFiles: {
                description: "从重写中排除这些文件。",
                oneOf: [
                  {
                    type: "string",
                  },
                  {
                    type: "array",
                    items: {
                      type: "string",
                    },
                  },
                ],
              },
              options: {
                type: "object",
                description: "用于应用此覆盖的选项。",
                $ref: "#/definitions/optionsDefinition",
              },
            },
            additionalProperties: false,
          },
        },
      },
    },
  },
  id: "https://json.schemastore.org/prettierrc.json",
  oneOf: [
    {
      type: "object",
      allOf: [
        {
          $ref: "#/definitions/optionsDefinition",
        },
        {
          $ref: "#/definitions/overridesDefinition",
        },
      ],
    },
    {
      type: "string",
    },
  ],
  title: "Schema for .prettierrc",
};

```
