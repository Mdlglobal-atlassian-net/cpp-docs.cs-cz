---
title: Array a WriteOnlyArray (C++/CX)
ms.date: 01/22/2017
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
ms.openlocfilehash: 2ade7981d391288edd78f622b4753d546c5eaa04
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740692"
---
# <a name="array-and-writeonlyarray-ccx"></a>Array a WriteOnlyArray (C++/CX)

V programu C++/CX můžete volně používat standardní pole ve stylu jazyka C nebo [std:: Array](../standard-library/array-class-stl.md) (i když je často lepší volbou [std:: Vector](../standard-library/vector-class.md) ), ale v jakémkoli rozhraní API, které je Publikováno v metadatech, je nutné převést pole nebo vektor ve stylu jazyka c na [Platform:: Array. ](../cppcx/platform-array-class.md)nebo typ [Platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) v závislosti na tom, jak se používá. Typ [Platform:: Array](../cppcx/platform-array-class.md) není ani účinný, ani jako účinný jako [std:: Vector](../standard-library/vector-class.md), takže jako obecné pokyny byste se měli vyhnout jeho použití v interním kódu, který provádí mnoho operací na prvcích Array.

Následující typy polí lze předat v rámci ABI:

1. const Platform:: Array ^

1. Platform:: Array ^ *

1. Platform:: WriteOnlyArray

1. Návratová hodnota platformy:: Array ^

Tyto typy polí použijete k implementaci tří druhů vzorů pole, které jsou definovány prostředí Windows Runtime.

PassArray se používá v případě, že volající předává pole do metody. C++ Vstupní typ parametru je `const` [Platform:: Array](../cppcx/platform-array-class.md)\<T >.

Metodě FillArray se používá, když volající předává pole pro metodu Fill. Typ C++ vstupního parametru je [Platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)\<T >.

ReceiveArray se používá v případě, že volající obdrží pole, které Metoda přiděluje. V C++/CX můžete vrátit pole v návratové hodnotě jako pole ^ nebo ho můžete vrátit jako výstupní parametr jako pole typu ^ *.

## <a name="passarray-pattern"></a>Vzor PassArray

Když klientský kód předá do C++ metody pole a metoda ho neupraví, metoda akceptuje pole jako const Array ^. Na úrovni prostředí Windows Runtimeho binárního rozhraní aplikace (ABI) se označuje jako PassArray. Další příklad ukazuje, jak předat pole, které je přiděleno v jazyce JavaScript, C++ do funkce, která z ní čte.

[!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]

Následující fragment kódu ukazuje C++ metodu:

[!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]

## <a name="receivearray-pattern"></a>Vzor ReceiveArray

Ve vzoru ReceiveArray kód klienta deklaruje pole a předá ho metodě, která pro ni přiděluje paměť a inicializuje ji. C++ Vstupní typ parametru je pointer-to-Hat: `Array<T>^*`. Následující příklad ukazuje, jak deklarovat objekt Array v JavaScriptu a předat ho C++ funkci, která přiděluje paměť, inicializuje prvky a vrátí ji do JavaScriptu. JavaScript považuje přidělené pole za návratovou hodnotu, ale C++ funkce ji zpracuje jako výstupní parametr.

[!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]

Následující fragment kódu ukazuje dva způsoby, jak implementovat C++ metodu:

[!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]

## <a name="fill-arrays"></a>Vyplnit pole

Pokud chcete přidělit pole v volajícím a inicializovat nebo upravit ho v volaném, použijte `WriteOnlyArray`. Další příklad ukazuje, jak implementovat C++ funkci, která používá `WriteOnlyArray` a volá ji z JavaScriptu.

[!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]

Následující fragment kódu ukazuje, jak implementovat C++ metodu:

[!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]

## <a name="array-conversions"></a>Převody polí

Tento příklad ukazuje, jak použít objekt [Platform:: Array](../cppcx/platform-array-class.md) k vytvoření dalších druhů kolekcí:

[!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]

Další příklad ukazuje, jak vytvořit objekt [Platform:: Array](../cppcx/platform-array-class.md) z pole ve stylu jazyka C a vrátit jej z veřejné metody.

[!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]

## <a name="jagged-arrays"></a>Vícenásobná pole

Systém typů prostředí Windows Runtime nepodporuje koncept vícenásobných polí, a proto jej nelze použít `IVector<Platform::Array<T>>` jako návratovou hodnotu nebo parametr metody ve veřejné metodě. Chcete-li předat vícenásobné pole nebo sekvenci sekvencí v rámci ABI, `IVector<IVector<T>^>`použijte.

## <a name="use-arrayreference-to-avoid-copying-data"></a>Vyhněte se kopírování dat pomocí ArrayReference

V některých případech, kdy se data předávají v rámci ABI do objektu [Platform:: Array](../cppcx/platform-array-class.md)a opravdu chcete zpracovat tato data v poli ve stylu jazyka C pro efektivitu, můžete použít [Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) , aby se zabránilo operaci nadbytečného kopírování. Pokud předáte [Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) jako argument parametru, který přijímá `Platform::Array`, `ArrayReference` uloží data přímo do pole ve stylu jazyka C, které zadáte. Stačí si uvědomit, `ArrayReference` že nemá žádný zámek ke zdrojovým datům, takže pokud se data upraví nebo odstraní v jiném vlákně, než se volání dokončí, výsledky se nedefinují.

Následující fragment kódu ukazuje, jak zkopírovat výsledky operace [DataReader](/uwp/api/Windows.Storage.Streams.DataReader) do `Platform::Array` (obvyklého vzoru) a následně nahradit `ArrayReference` data přímo do pole ve stylu jazyka C:

[!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]

## <a name="avoid-exposing-an-array-as-a-property"></a>Vyhněte se vystavení pole jako vlastnosti

Obecně byste se měli vyhnout `Platform::Array` vystavení typu jako vlastnost v referenční třídě, protože celé pole je vráceno i v případě, že se kód klienta pokouší o přístup pouze k jednomu prvku. Pokud potřebujete zveřejnit kontejner sekvence jako vlastnost ve veřejné referenční třídě, [Windows:: Foundation:: IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) je lepší volbou. V privátních nebo interních rozhraních API (která nejsou publikována v metadatech) C++ zvažte použití standardního kontejneru, jako je například [std:: Vector](../standard-library/vector-class.md).

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
