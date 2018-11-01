---
title: 'Postupy: Poskytování pracovních funkcí třídám call a transformer'
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: d9d472ddd8d5c7baf3cb16e1df33a2bdb74c5381
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500997"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Postupy: Poskytování pracovních funkcí třídám call a transformer

Toto téma ukazuje několik způsobů, jak poskytování pracovních funkcí k [concurrency::call](../../parallel/concrt/reference/call-class.md) a [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) třídy.

První příklad ukazuje, jak předat výraz lambda, který má `call` objektu. Druhý příklad ukazuje, jak předat objekt a funkce `call` objektu. Třetí příklad ukazuje, jak metody třídy pro vytvoření vazby `call` objektu.

Pro ilustraci, každý příklad v tomto tématu používá `call` třídy. Příklad, který se používá `transformer` najdete v tématu [postupy: použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje běžný způsob, jak používat `call` třídy. Tento příklad předává lambda funkce `call` konstruktoru.

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
13 squared is 169.
```

## <a name="example"></a>Příklad

Následující příklad se podobá předchozímu, s tím rozdílem, že používá `call` třída objektu – funkce (funktoru).

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>Příklad

Následující příklad se podobá předchozímu, s tím rozdílem, že používá [std::bind1st](../../standard-library/functional-functions.md#bind1st) a [std::mem_fun](../../standard-library/functional-functions.md#mem_fun) funkce k vytvoření vazby `call` objekt pro metodu třídy.

Tento postup použijte, pokud je nutné vytvořit vazbu `call` nebo `transformer` objektu metodě konkrétní třídu namísto operátoru volání funkce `operator()`.

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

Můžete také přiřadit výsledek `bind1st` funkce [std::function](../../standard-library/function-class.md) objektu nebo použijte `auto` – klíčové slovo, jak je znázorněno v následujícím příkladu.

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `call.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc call.cpp**

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Postupy: Použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call – třída](../../parallel/concrt/reference/call-class.md)<br/>
[transformer – třída](../../parallel/concrt/reference/transformer-class.md)
