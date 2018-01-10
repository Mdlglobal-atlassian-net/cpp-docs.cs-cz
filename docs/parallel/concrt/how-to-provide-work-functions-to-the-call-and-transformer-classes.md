---
title: "Postupy: poskytování pracovních funkcí třídám call a transformer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52ab28a015fa0312a5d064401451640c2747e9db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Postupy: Poskytování pracovních funkcí třídám call a transformer
Toto téma znázorňuje několik způsobů, jak poskytování pracovních funkcí k [concurrency::call](../../parallel/concrt/reference/call-class.md) a [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) třídy.  
  
 V prvním příkladu ukazuje, jak k předání do výrazu lambda `call` objektu. Druhý příklad ukazuje, jak předat objekt a funkce `call` objektu. Třetí příklad ukazuje, jak vytvořit vazbu třída metodu pro `call` objektu.  
  
 Pro ilustraci, každý příklad v tomto tématu používá `call` třídy. Pro příklad, který používá `transformer` třídy najdete v tématu [postupy: použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje běžný způsob použití `call` třídy. Tento příklad předá lambda funkce, která se `call` konstruktor.  
  
 [!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
13 squared is 169.  
```  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se podobá předchozímu, s tím rozdílem, že se používá `call` třída společně s objekt funkce (functor).  
  
 [!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]  
  
## <a name="example"></a>Příklad  

 V následujícím příkladu se podobá předchozímu, s tím rozdílem, že se používá [std::bind1st](../../standard-library/functional-functions.md#bind1st) a [std::mem_fun](../../standard-library/functional-functions.md#mem_fun) funkce pro vazbu `call` objekt metody třídy.  

  
 Tento postup použijte, pokud máte k vytvoření vazby `call` nebo `transformer` objekt, který má metoda určité třídy místo operátor volání funkce `operator()`.  
  
 [!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]  
  
 Je také možné přiřadit výsledek `bind1st` funkci, aby se [std::function](../../standard-library/function-class.md) objektu nebo použít `auto` – klíčové slovo, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `call.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc call.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Postupy: použití transformace v datovém kanálu](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)   
 [Call – třída](../../parallel/concrt/reference/call-class.md)   
 [transformer – třída](../../parallel/concrt/reference/transformer-class.md)
