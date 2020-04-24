---
title: Pole a WriteOnlyArray (C++/CX)
ms.date: 01/22/2017
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
ms.openlocfilehash: e050fad38d4f70c651fc0ebfddb51a33e31da6f3
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032405"
---
# <a name="array-and-writeonlyarray-ccx"></a>Pole a WriteOnlyArray (C++/CX)

Můžete volně používat běžné pole ve stylu C nebo [std::array](../standard-library/array-class-stl.md) v programu C++/CX (i když [std::vector](../standard-library/vector-class.md) je často lepší volbou), ale v každém rozhraní API, které je publikováno v metadatech, je nutné převést pole nebo vektor ve stylu C na [platformu::Array](../cppcx/platform-array-class.md) nebo [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) typ v závislosti na tom, jak se používá. [Typ Platform::Array](../cppcx/platform-array-class.md) není ani tak efektivní, ani tak výkonný jako [std::vector](../standard-library/vector-class.md), takže jako obecné vodítko byste se měli vyhnout jeho použití v interním kódu, který provádí velké množství operací na prvky pole.

Následující typy polí mohou být předány přes ABI:

1. const Platform::Array^

1. Platforma::Array^*

1. Platforma::WriteOnlyArray

1. vrácená hodnota platformy::Array^

Tyto typy polí slouží k implementaci tří druhů vzorů pole, které jsou definovány prostředím Windows Runtime.

PassArray Používá se, když volající předá pole metodě. Typ vstupního parametru `const`C++ je [platforma::Array](../cppcx/platform-array-class.md)\<T>.

FillArray Používá se, když volající předá pole pro metodu vyplnit. Typ vstupního parametru C++ je [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)\<T>.

ReceiveArray Používá se, když volající obdrží pole, které metoda přiděluje. V jazyce C++/CX můžete vrátit pole v návratové hodnotě jako pole^ nebo jej můžete vrátit jako out parametr jako typ Array^*.

## <a name="passarray-pattern"></a>PassArray vzor

Pokud klientský kód předá pole metodě Jazyka C++ a metoda ji nezmění, metoda přijme pole jako const Array^. Na úrovni binárního rozhraní aplikace Prostředí Windows Runtime (ABI) se toto nazývá PassArray. Následující příklad ukazuje, jak předat pole, které je přiděleno v Jazyce JavaScript u funkce Jazyka C++, která z něj čte.

[!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]

Následující úryvek ukazuje metodu C++:

[!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]

## <a name="receivearray-pattern"></a>Vzorek ReceiveArray

Ve vzoru ReceiveArray klientský kód deklaruje pole a předá ho metodě, která pro něj přiděluje paměť a inicializuje ji. Typ vstupního parametru C++ je ukazatel `Array<T>^*`na klobouk: . Následující příklad ukazuje, jak deklarovat objekt pole v Jazyce JavaScript a předat jej funkci C++, která přiděluje paměť, inicializuje prvky a vrací jej do Jazyka JavaScript. JavaScript považuje přidělené pole za vrácenou hodnotu, ale funkce C++ s ním zachází jako s parametrem out.

[!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]

Následující úryvek ukazuje dva způsoby implementace metody Jazyka C++:

[!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]

## <a name="fill-arrays"></a>Vyplnit pole

Pokud chcete přidělit pole volajícího a inicializovat nebo upravit v `WriteOnlyArray`volaný, použijte . Následující příklad ukazuje, jak implementovat funkci `WriteOnlyArray` Jazyka C++, která ji používá a volá z JavaScriptu.

[!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]

Následující úryvek ukazuje, jak implementovat metodu C++:

[!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]

## <a name="array-conversions"></a>Převody polí

Tento příklad ukazuje, jak používat [platformu::Array](../cppcx/platform-array-class.md) k vytvoření jiných druhů kolekcí:

[!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]

Následující příklad ukazuje, jak vytvořit [Platform::Array](../cppcx/platform-array-class.md) z pole ve stylu C a vrátit jej z veřejné metody.

[!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]

## <a name="jagged-arrays"></a>Zubatá pole

Systém typu Prostředí Windows Runtime nepodporuje koncept zubatých polí, a proto nelze použít `IVector<Platform::Array<T>>` jako parametr návratové hodnoty nebo metody ve veřejné metodě. Chcete-li předat zubaté pole nebo posloupnost `IVector<IVector<T>^>`sekvencí přes ABI, použijte .

## <a name="use-arrayreference-to-avoid-copying-data"></a>Chcete-li se vyhnout kopírování dat, použijte ArrayReference.

V některých scénářích, kde jsou data předávána přes ABI do [platformy::Array](../cppcx/platform-array-class.md)a nakonec chcete zpracovat tato data v poli ve stylu C pro efektivitu, můžete použít [Platform::ArrayReference,](../cppcx/platform-arrayreference-class.md) abyste se vyhnuli operaci další kopie. Když předáte [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) jako argument `Platform::Array`parametru, který `ArrayReference` trvá , uloží data přímo do pole ve stylu C, které zadáte. Jen si `ArrayReference` uvědomte, že nemá zámek na zdrojová data, takže pokud je tato data upravena nebo odstraněna v jiném vlákně před dokončením volání, výsledky nebudou definovány.

Následující fragment kódu ukazuje, jak zkopírovat výsledky operace [DataReader](/uwp/api/windows.storage.streams.datareader) do `Platform::Array` (obvyklý vzor) a `ArrayReference` potom jak nahradit zkopírování dat přímo do pole ve stylu C:

[!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]

## <a name="avoid-exposing-an-array-as-a-property"></a>Vyhněte se vystavení pole jako vlastnosti

Obecně byste se měli vyhnout `Platform::Array` vystavení typu jako vlastnosti ve třídě ref, protože celé pole je vráceno, i když se klientský kód pokouší pouze o přístup k jednomu prvku. Když potřebujete vystavit kontejner sekvence jako vlastnost ve veřejné třídě ref, [Windows::Foundation::IVector](/uwp/api/windows.foundation.collections.ivector-1) je lepší volbou. V soukromých nebo interních api (které nejsou publikovány do metadat) zvažte použití standardního kontejneru C++, například [std::vector](../standard-library/vector-class.md).

## <a name="see-also"></a>Viz také

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
