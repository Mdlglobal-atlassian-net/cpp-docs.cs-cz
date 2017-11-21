---
title: Pole a WriteOnlyArray (C + +/ CX) | Microsoft Docs
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
caps.latest.revision: "28"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 181dcba15098f7cd75eec083ab977969bde622ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="array-and-writeonlyarray-ccx"></a>Pole a WriteOnlyArray (C + +/ CX)
Můžete volně používat regulární pole stylu jazyka C nebo [std::array](../standard-library/array-class-stl.md) v jazyce C + +/ CX program (i když [std::vector](../standard-library/vector-class.md) je často lepší volbou), ale v jakéhokoli rozhraní API, která je publikovaná v metadatech, je nutné převést pole ve stylu jazyka C nebo vector k [Platform::Array](../cppcx/platform-array-class.md) nebo [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) typu v závislosti na tom, jak je používán. [Platform::Array](../cppcx/platform-array-class.md) typ není jako efektivní ani výkonné jako [std::vector](../standard-library/vector-class.md), takže v rámci obecných pokynů byste neměli jeho použití v interní kód, který provádí velké množství operací na pole elementy.  
  
 Následující typy pole může být předán přes ABI:  
  
1.  Const Platform::Array ^  
  
2.  Platform::Array ^ *  
  
3.  Platform::WriteOnlyArray  
  
4.  Návratová hodnota Platform::Array ^  
  
 Můžete používat tyto typy pole implementovat tři druhy vzory pole, které jsou definovány pomocí prostředí Windows Runtime.  
  
 PassArray  
 Použít tehdy, když volání pole na metodu. Typ vstupního parametru C++ je `const` [Platform::Array](../cppcx/platform-array-class.md)\<T >.  
  
 FillArray  
 Použít tehdy, když volání pro metodu k vyplnění pole. Typ vstupního parametru C++ je [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)\<T >.  
  
 ReceiveArray  
 Použít pole, které metody přiděluje přijetí volající. V jazyce C + +/ CX může vrátit pole v návratovou hodnotu jako pole ^ nebo ho můžete vrátit jako výstupní parametr jako typ pole ^ *.  
  
## <a name="passarray-pattern"></a>Vzor PassArray  
 Když klientský kód předá pole metodě C++ a metodu neupravuje, metoda přijímá pole jako const pole ^. Na úrovni aplikace binární rozhraní (ABI) prostředí Windows Runtime to se označuje jako PassArray. Další příklad ukazuje, jak předat pole, které je přiděleno v jazyce JavaScript C++ funkci, která načte z něj.  
  
 [!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]  
  
 Následující fragment kódu ukazuje metodu C++:  
  
 [!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]  
  
## <a name="receivearray-pattern"></a>Vzor ReceiveArray  
 Ve vzoru ReceiveArray kód klienta deklaruje pole a předává je na metodu, která přidělí paměť a inicializaci. Typ vstupního parametru C++ je ukazatel na hat: `Array<T>^*`. Následující příklad ukazuje, jak deklarace objektu pole v jazyce JavaScript a předejte ji do C++ funkci, která se přidělí paměť, inicializuje elementy a vrátí ji do jazyka JavaScript. JavaScript zpracovává přidělené pole jako typ návratové hodnoty, ale funkce C++ pracuje s ním jako výstupní parametr.  
  
 [!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]  
  
 Následující fragment kódu ukazuje dva způsoby, jak implementovat metodu C++:  
  
 [!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]  
  
## <a name="fill-arrays"></a>Vyplnění polí  
 Pokud chcete přidělit pole v volající a inicializaci nebo ho můžete upravit v volaného, použijte `WriteOnlyArray`. Další příklad ukazuje, jak implementovat funkci C++, která používá `WriteOnlyArray` a volání z jazyka JavaScript.  
  
 [!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]  
  
 Následující fragment kódu ukazuje, jak implementovat metodu C++:  
  
 [!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]  
  
## <a name="array-conversions"></a>Převody pole  
 Tento příklad ukazuje, jak používat [Platform::Array](../cppcx/platform-array-class.md) vytvořit další typy kolekcí:  
  
 [!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]  
  
 Další příklad ukazuje, jak vytvořit [Platform::Array](../cppcx/platform-array-class.md) z stylu jazyka C pole a obnoví v něm z veřejné metody.  
  
 [!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]  
  
## <a name="jagged-arrays"></a>Vícenásobná pole  
 Systém typů prostředí Windows Runtime nepodporuje koncept Vícenásobná pole, takže nemůže používat `IVector<Platform::Array<T>>` jako návratovou hodnotu nebo metoda parametr veřejná metoda. Chcete-li předat Vícenásobná pole nebo posloupnost pořadí napříč ABI, použijte `IVector<IVector<T>^>`.  
  
## <a name="use-arrayreference-to-avoid-copying-data"></a>Pomocí ArrayReference vyhnout kopírování dat  
 V některých scénářích, kde je data předávána napříč ABI do [Platform::Array](../cppcx/platform-array-class.md)a nakonec chcete ke zpracování dat v poli stylu jazyka C pro účinnost, můžete použít [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) aby se zabránilo další kopírování. Pokud předáte [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) jako argument pro parametr, který přebírá `Platform::Array`, `ArrayReference` se uloží data přímo ve stylu jazyka C pole, které zadáte. Právě mějte na paměti, `ArrayReference` má žádné zámku na zdrojová data, takže pokud data jsou upravit nebo odstranit v jiné vlákno před dokončením volání, výsledky nedefinovaný.  
  
 Následující fragment kódu ukazuje, jak zkopírovat výsledky [DataReader –](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.datareader.aspx) operace do `Platform::Array` (obvykle vzor) a poté jak nahradit `ArrayReference` ke zkopírování dat přímo do pole stylu jazyka C:  
  
 [!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]  
  
## <a name="avoid-exposing-an-array-as-a-property"></a>Vyhněte se vystavení pole jako vlastnost  
 Obecně platí, neměli byste vystavení `Platform::Array` zadejte jako vlastnost v třídě ref, protože je vrátil celé pole, i v případě, že kód klienta se pouze pokouší o přístup na jeden element. Pokud je nutné vystavit kontejner pořadí jako vlastnost v třídě veřejné ref [Windows::Foundation::IVector](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) je lepší volbou. V privátní nebo interní rozhraní API (které nejsou vydané ve službě metadata), zvažte použití standardního kontejner C++, jako [std::vector](../standard-library/vector-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)