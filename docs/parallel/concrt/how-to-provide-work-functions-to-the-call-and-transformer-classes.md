---
title: 'Postupy: Poskytování pracovních funkcí třídám call a transformer'
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: 4d2b7b3c88b51003a96526ef14d9940a8c26c3b3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142492"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Postupy: Poskytování pracovních funkcí třídám call a transformer

Toto téma ukazuje několik způsobů, jak poskytnout pracovní funkce třídám [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) a [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) .

První příklad ukazuje, jak předat výraz lambda do objektu `call`. Druhý příklad ukazuje, jak předat objekt funkce objektu `call`. Třetí příklad ukazuje, jak vytvořit svázání metody třídy s objektem `call`.

Pro ilustraci každý příklad v tomto tématu používá třídu `call`. Příklad, který používá třídu `transformer`, naleznete v tématu [How to: use in the data Pipeline](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje běžný způsob použití třídy `call`. Tento příklad předá funkci lambda konstruktoru `call`.

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
13 squared is 169.
```

## <a name="example"></a>Příklad

Následující příklad je podobný předchozímu, s tím rozdílem, že používá třídu `call` společně s objektem funkce (funktor).

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>Příklad

Následující příklad je podobný předchozímu, s tím rozdílem, že používá funkce [std:: bind1st –](../../standard-library/functional-functions.md#bind1st) a [std:: mem_fun](../../standard-library/functional-functions.md#mem_fun) pro svázání objektu `call` s metodou třídy.

Tuto techniku použijte, pokud je třeba vytvořit vazby `call` nebo `transformer` objektu na konkrétní metodu třídy namísto operátoru volání funkce `operator()`.

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

Výsledek funkce `bind1st` lze také přiřadit objektu [std:: Function](../../standard-library/function-class.md) nebo použít klíčové slovo `auto`, jak je znázorněno v následujícím příkladu.

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `call.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc volání. cpp**

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Postupy: Použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call – třída](../../parallel/concrt/reference/call-class.md)<br/>
[transformer – třída](../../parallel/concrt/reference/transformer-class.md)
