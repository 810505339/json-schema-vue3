<script setup lang="ts">
import type { JSONSchemaType } from 'ajv'
import { zh } from 'ajv-i18n'
import Ajv from 'ajv'
const ajv = new Ajv()

interface MyData {
  foo: number
  bar?: string
}

const schema: JSONSchemaType<MyData> = {
  type: 'object',
  properties: {
    foo: { type: 'integer' },
    bar: { type: 'string', nullable: true },
  },
  required: ['foo'],
  additionalProperties: false,
}
const validate = ajv.compile(schema)
const data = {
  foo: '',
  bar: 'abc',
}

if (validate(data)) {
  // data is MyData here
  console.log(data.foo)
}
else {
  zh(validate.errors)
  console.log(ajv.errorsText(validate.errors, { separator: '\n' }))
}
</script>

<template />
