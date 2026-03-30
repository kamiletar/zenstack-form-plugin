# Changelog

## [1.0.0] - 2026-03-31

### Features

- Generate Zod v4 schemas with `.meta({ ui: {...} })` from `schema.zmodel`
- Support `@form.*` directives: title, placeholder, description, fieldType, props, relation, exclude
- Auto-split `@form.props` into Zod constraints (min, max, email) and UI props (count, showValue)
- Enum generation with labels from `///` doc comments
- Model generation with Create/Update schemas and excluded fields list
- i18n support: generate translation JSON files per locale with merge strategy
- Auto-exclude: id, createdAt, updatedAt, @relation fields
- Compatible with `@letar/forms` (`Form.FromSchema`, `Form.Field.*`)
