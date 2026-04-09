# @letar/zenstack-form-plugin

ZenStack плагин для генерации Zod схем с UI метаданными из `schema.zmodel`.

[![npm version](https://img.shields.io/npm/v/@letar/zenstack-form-plugin)](https://www.npmjs.com/package/@letar/zenstack-form-plugin)
[![license](https://img.shields.io/npm/l/@letar/zenstack-form-plugin)](./LICENSE)

📖 [Forms Documentation](https://forms.letar.best) · 🎮 [Live Examples](https://forms-example.letar.best/examples/zenstack) · 📦 [@letar/forms](https://www.npmjs.com/package/@letar/forms)

**Before:** describe entity 3 times (Prisma model + Zod schema + JSX form)
**After:** describe once in `schema.zmodel` with `@form.*` directives → everything is generated

[English documentation](./README.en.md)

## Установка

```bash
npm install -D @letar/zenstack-form-plugin
```

## Конфигурация

Добавьте плагин в `schema.zmodel`:

```zmodel
plugin formSchema {
  provider = '@letar/zenstack-form-plugin'
  output = './src/generated/form-schemas'
}
```

## Быстрый пример

```zmodel
model Product {
  id    String @id @default(cuid())

  /// @form.title("Название продукта")
  /// @form.placeholder("Введите название")
  title String

  /// @form.title("Цена")
  /// @form.fieldType("currency")
  /// @form.props({ min: 0, currency: "RUB" })
  price Int
}
```

→ Генерирует `ProductCreateFormSchema` и `ProductUpdateFormSchema` с Zod v4 + `.meta({ ui })`.

## Поддерживаемые директивы

| Директива                  | Описание            | Пример                                       |
| -------------------------- | ------------------- | -------------------------------------------- |
| `@form.title("...")`       | Заголовок поля      | `/// @form.title("Название")`                |
| `@form.placeholder("...")` | Placeholder         | `/// @form.placeholder("Введите...")`        |
| `@form.description("...")` | Описание поля       | `/// @form.description("Подсказка")`         |
| `@form.fieldType("...")`   | Тип компонента      | `/// @form.fieldType("tags")`                |
| `@form.props({...})`       | Constraints + props | `/// @form.props({ min: 1, max: 100 })`      |
| `@form.relation({...})`    | Настройки relation  | `/// @form.relation({ labelField: "name" })` |
| `@form.exclude`            | Исключить из формы  | `/// @form.exclude`                          |

Полная документация директив: [forms.letar.best/docs/guides/zenstack-plugin](https://forms.letar.best/docs/guides/zenstack-plugin)

## AI Tooling (MCP)

MCP сервер [`@letar/form-mcp`](https://www.npmjs.com/package/@letar/form-mcp) предоставляет AI-ассистентам доступ к документации всех `@form.*` директив через tool `get_directives`.

## Версия

v2.1.0
