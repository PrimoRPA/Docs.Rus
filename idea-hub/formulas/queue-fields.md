# Поля очереди

## Очередь

**Тип поля**: Entity reference

**Машинное имя**: field_queue

**Описание**: Вы можете связать с данным процессом несколько очередей, однако данные для расчётов будут браться только из первой очереди из списка. Для изменения порядка следования очередей в списке, вы можете перемещать их с помощью перетаскивания.

## Плановый эффект, в месяц

**Тип поля**: Формула

**Машинное имя**: field_revenue_expected

**Описание**: Нет описания

**Формула**

```
this.field_fte_savings * this.field_fte_human_fte_cost * SALARY_INCREASE_FACTOR
```

## Фактический эффект

**Тип поля**: Формула

**Машинное имя**: field_revenue_real

**Описание**: Эффект в деньгах.

**Формула**

```
this.field_fte * this.field_fte_human_fte_cost * SALARY_INCREASE_FACTOR
```

### Отображение default
**Тип**: delta_formatter

**Настройки**: 
```
vars:
  value: avg(this.field('field_revenue_real', null, 'last day of previous month', 'month', 'sum'))
  delta:  value - this.field_revenue_expected
exp: |
  {"value": value, "delta": delta} 
```

## Revision date

**Тип поля**: Дата

**Машинное имя**: field_revision_date

**Описание**: The date of current revision. Entity store historical stat and calculated data for this date.
