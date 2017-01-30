# Sudoku
### Алгоритм решения:
#### Общие моменты
Поле `Field` представляет собой стек, состоящий из самого поля `fields` - двумерный массив из клеточек `FieldElement`, ссылки на предыдущий элемент ` Field prevField` и точки `Point`, которая указывает, какую клеточку мы сейчас изменили и на какое значение.
Для каждой клеточки создается список из всевозможных чисел, которые могут находиться в данной ячейке. Соответственно, если клеточка первоначально заполнена, то список пустой.
#### Алгоритм
1. Проходимся по всему полю и удаляем из списков все элементы, которые уже стоят в строке, столбце или блоке.
2. Если в списке остался всего один элемент, то заполняем ячейку, плюс, считаем количество таких изменений.
3. Проверяем на то, что поле осталось корректным (нет повторяющихся цифр в строке, столбце, блоке), иначе откатываемся назад по стеку.
4. Если изменений нет, и не осталось пустых ячеек, то откатываемся назад.
5. Если остались пустые ячейки, то берем первую свободную, устанавливаем ее значение первым из списка доступных и добавляем на вершину стека.

#### Проверка на завершение
Все списки должны быть пустыми, и не должно остаться пустых клеточек. Соответственно, предполагается, что решение есть. Если решений несколько (что, по идее, не должно быть), то найдется первое. Также есть ограничение на количество итераций цикла (2000), которое, при правильной работе (и прямых руках), не должно сработать.
