## Структура manifest.json

Данный файл - пожалуй, самый главный для любого модуля. 
Он описывает все важные глобальные настройки модуля, всю информацию, типы действий и их названия, а так же локализацию.

Представляет из себя текстовый файл с контентом в формате **JSON**. Вот элементарный пример:

```javascript
{
	"name":"[0]",
	"info":
	{
		"en": "[1]", 
		"ru": "[2]"
	},
	"icon": "[3]",
	"description":"[4]",
	"description_small":
	{
		"en": "[5]", 
		"ru": "[6]"
	},
	"major_version": [7],
	"minor_version": [8],
	"developer_name": "[9]", 
	"developer_email": "[10]", 
	"developer_site": "[11]",
	"api_version": [12],
	"actions": [],
	"localize": {},
	"engine": [],
	"browser": [],
	"depends": []	
}
```

## Структура
