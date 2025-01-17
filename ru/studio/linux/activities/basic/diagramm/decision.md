# Принятие решения

![](../../resources/basic/diagramm/image-(100)-(1)-(1)-(1)-(1)-(1)-(1)-(1)-(2)-(37).png)

![](../../resources/basic/diagramm/image-(325).png)

**Принятие решения** служит для разветвления выполнения процесса (аналогично конструкции Switch классических языков программирования). Выбор пути для выполнения того или иного алгоритма зависит от результата вычисляемого выражения. При этом путей может быть более двух - см. рисунок ниже:

![](../../resources/basic/diagramm/пример-принятия-решения.png)

**Обратите внимание**, что проверяемое выражение (условие) задается в свойствах элемента **Принятие решения**:

> _Описание общих свойств см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство  | Тип                                                                                                     | Описание                                                                 |
| --------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| Условие\* | [T](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/generics/generic-type-parameters) | Укажите выражение, которое нужно проверить перед выбором одного из путей |

А возможные результаты этого выражения - в свойствах связей, т. е. в стрелках, ведущих от **Принятия решения** к тому или иному компоненту. Чтобы указать результат, нажмите на конкретную стрелку и введите нужное значение в свойстве **Результат проверки**. Если результат выражения не совпал ни с одним значением, заданным в свойствах связей, то выполнится та стрелка, для которой результат не задан - она будет считаться путем по умолчанию.

{% content-ref url="../../../primo-studio/process/diagram.md" %}
[diagram.md](../../../primo-studio/process/diagram.md)
{% endcontent-ref %}
