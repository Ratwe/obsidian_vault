Функция `CreateThread` используется для создания нового потока в процессе. Это позволяет вашему приложению выполнять несколько задач одновременно, что может улучшить производительность, особенно для задач, которые могут быть выполнены параллельно [Source 0](https://learn.microsoft.com/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread).

```c
for (int i = 0; i < WRITERS_COUNT; ++i)
{
	process_nums[i] = i + 1;
	thread_handler[i] = CreateThread(NULL, 0, writer, &process_nums[i], 0, &thread_id[i]);
	if (thread_handler[i] == NULL)
	{
		perror("Can't create writer thread");
		exit(EXIT_FAILURE);
	}
}
```

В вашем коде `CreateThread` используется для создания потоков записи. Каждый поток записи выполняет функцию `writer`, которая, вероятно, записывает данные в какой-то общий ресурс. Параметр `&process_nums[i]` передается в функцию `writer` как аргумент, и, вероятно, используется для указания номера процесса.

Параметр `0` указывает на то, что поток будет использовать размер стека по умолчанию. Параметр `0` указывает на то, что поток будет создаваться в состоянии готовности к выполнению (не приостановлен). Параметр `&thread_id[i]` используется для получения идентификатора потока, который затем сохраняется в массиве `thread_id`.

Если функция `CreateThread` возвращает `NULL`, это означает, что поток не был успешно создан. В этом случае выводится сообщение об ошибке и программа завершается с кодом ошибки [Source 0](https://learn.microsoft.com/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread).

Вот пример использования `CreateThread`:

```cpp
HANDLE thread_handler = CreateThread(NULL, 0, writer, &process_nums[i], 0, &thread_id[i]);
if (thread_handler == NULL)
{
   perror("Can't create writer thread");
   exit(EXIT_FAILURE);
}
```

В этом примере `CreateThread` вызывается для создания нового потока, который выполняет функцию `writer`. Если поток не может быть создан, выводится сообщение об ошибке и программа завершается с кодом ошибки. [[HANDLE]].

### Links
[[Потоки]], [[Windows API]]