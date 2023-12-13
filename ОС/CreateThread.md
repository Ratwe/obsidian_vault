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

Функция `CreateThread` в Windows используется для создания нового потока в процессе. Вот параметры, которые принимает эта функция:

1. `lpThreadAttributes`: Этот параметр является необязательным и указывает на структуру `SECURITY_ATTRIBUTES`, которая содержит атрибуты безопасности для нового потока. Если этот параметр равен `NULL`, то поток создается с атрибутами безопасности по умолчанию [Source 0](https://learn.microsoft.com/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread).
2. `dwStackSize`: Этот параметр указывает начальный размер стека для нового потока. Если этот параметр равен `0`, то размер стека по умолчанию [Source 0](https://learn.microsoft.com/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread).
3. `lpStartAddress`: Этот параметр указывает на функцию, которую должен выполнить новый поток. Функция должна быть определена как `LPTHREAD_START_ROUTINE`, то есть она должна возвращать `DWORD` и принимать один аргумент типа `LPVOID` [Source 0](https://learn.microsoft.com/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread).
4. `lpParameter`: Этот параметр является необязательным и указывает на аргумент, который будет передан в функцию `lpStartAddress` [Source 0](https://learn.microsoft.com/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread).
5. `dwCreationFlags`: Этот параметр указывает флаги создания потока. Например, `CREATE_SUSPENDED` создает поток в приостановленном состоянии, который не начинает выполнение до тех пор, пока не будет вызван `ResumeThread` [Source 0](https://learn.microsoft.com/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread).
6. `lpThreadId`: Этот параметр является необязательным и указывает на переменную, в которую будет записано идентификатор нового потока [Source 0](https://learn.microsoft.com/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread).

Если функция `CreateThread` успешно выполняется, она возвращает дескриптор нового потока. Если функция не выполняется, она возвращает `NULL` [Source 0](https://learn.microsoft.com/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread).

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