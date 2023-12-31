```c
HANDLE readers_threads[READERS_NUM];
HANDLE writers_threads[WRITERS_NUM];
```

В данном контексте `HANDLE` используется для создания массива дескрипторов потоков. `HANDLE` - это тип данных, используемый в [[Windows API]] для представления указателей на различные системные ресурсы, такие как файлы, потоки, окна и т.д. [Source 0](https://stackoverflow.com/questions/902967/what-is-a-windows-handle).

В данном случае, `HANDLE readers_threads[READERS_NUM];` и `HANDLE writers_threads[WRITERS_NUM];` создают массивы дескрипторов потоков. `READERS_NUM` и `WRITERS_NUM` - это константы, которые определяют количество потоков-читателей и потоков-писателей соответственно.

Каждый элемент этих массивов представляет собой дескриптор потока, который может быть использован для управления потоком (например, для ожидания завершения потока или для отправки сигнала потоку) [Source 1](https://learn.microsoft.com/en-us/windows/win32/sysinfo/handles-and-objects).

Важно отметить, что дескрипторы потоков не являются указателями на структуры потоков. Они являются абстрактными значениями, которые используются для идентификации потоков в системе. Значения этих дескрипторов не имеют смысла без контекста. Они должны быть рассмотрены как прозрачные значения, имеющие смысл только для API [Source 0](https://stackoverflow.com/questions/902967/what-is-a-windows-handle).

### Links
[[Потоки]]