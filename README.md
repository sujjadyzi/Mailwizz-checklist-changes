# Mailwizz-checklist-changes

File changes:

1. apps\common\models\ListFieldOption.php

```php
//Put these lines in rules function.
['anchor_text', 'length', 'max'=>1000],
['anchor_url', 'length', 'max'=>1000],


// Put these lines in attributeLabels function.
'anchor_text'   => t('list_fields', 'Anchor text'),
'anchor_url'    => t('list_fields', 'URL'),

```
2. apps\customer\components\list-field-builder\checkboxlist\views\field-tpl-js.php

Replace the div with class "checkboxlist-option-row": Probably start from line 111

```php
<div class="row">
  <div class="col-lg-3">
      <div class="form-group">
          <?php echo CHtml::activeLabelEx($option, 'name'); ?>
          <?php echo CHtml::textField($option->getModelName() . '[' . $fieldType->identifier . '][{parentIndex}][{optionIndex}][name]', null, $option->getHtmlOptions('name')); ?>
          <?php echo CHtml::error($option, 'name'); ?>
      </div>
  </div>
  <div class="col-lg-2">
      <div class="form-group">
          <?php echo CHtml::activeLabelEx($option, 'value'); ?>
          <?php echo CHtml::textField($option->getModelName() . '[' . $fieldType->identifier . '][{parentIndex}][{optionIndex}][value]', null, $option->getHtmlOptions('value')); ?>
          <?php echo CHtml::error($option, 'value'); ?>
      </div>
  </div>
  <div class="col-lg-2">
      <div class="form-group">
          <?php echo CHtml::activeLabelEx($option, 'Anchor text'); ?>
          <?php echo CHtml::textField($option->getModelName() . '[' . $fieldType->identifier . '][{parentIndex}][{optionIndex}][anchor_text]', null, $option->getHtmlOptions('anchor_text')); ?>
          <?php echo CHtml::error($option, 'Anchor text'); ?>
      </div>
  </div>
  <div class="col-lg-3">
      <div class="form-group">
          <?php echo CHtml::activeLabelEx($option, 'URL'); ?>
          <?php echo CHtml::textField($option->getModelName() . '[' . $fieldType->identifier . '][{parentIndex}][{optionIndex}][anchor_url]', null, $option->getHtmlOptions('anchor_url')); ?>
          <?php echo CHtml::error($option, 'URL'); ?>
      </div>
  </div>
  <div class="col-lg-2">
      <div class="pull-left" style="margin-top: 25px;">
          <a href="javascript:;" class="btn btn-danger btn-flat btn-remove-checkboxlist-option-field" data-option-id="0" data-message="<?php echo t('list_fields', 'Are you sure you want to remove this option? There is no coming back from this after you save the changes.'); ?>"><?php echo IconHelper::make('delete'); ?></a>
      </div>
  </div>
</div>
```
3. apps\customer\components\list-field-builder\checkboxlist\views\field-tpl.php
