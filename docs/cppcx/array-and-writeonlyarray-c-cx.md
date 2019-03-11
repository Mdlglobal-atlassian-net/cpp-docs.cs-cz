---
title: Pole a WriteOnlyArray (C + +/ CX)
ms.date: 01/22/2017
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
ms.openlocfilehash: fd616487bd3c11544f12e84a7dc64f41e63d501a
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739411"
---
# <a name="array-and-writeonlyarray-ccx"></a>Pole a WriteOnlyArray (C + +/ CX)

Lze volně používat regulární pole stylu C nebo [std::array](../standard-library/array-class-stl.md) v jazyce C + +/ CX programu (i když [std::vector](../standard-library/vector-class.md) je často vhodnější), ale v žádné rozhraní API, který je publikován v metadatech, je nutné převést pole stylu C nebo pro vektorové [Platform::Array](../cppcx/platform-array-class.md) nebo [Platform::writeonlyarray –](../cppcx/platform-writeonlyarray-class.md) typ v závislosti na tom, jak se používá. [Platform::Array](../cppcx/platform-array-class.md) typ není tak účinné ani výkonné jako funkce [std::vector](../standard-library/vector-class.md), takže se v rámci obecných pokynů byste se měli vyhnout použití ve vnitřní kód, který provádí mnoho operací s poli elementy.

Následující typy polí může být předán přes ABI:

1. Const Platform::Array ^

1. Platform::Array ^ *

1. Platform::writeonlyarray –

1. Návratová hodnota Platform::Array ^

Tyto typy polí můžete implementovat tři druhy vzory pole, které jsou definovány pomocí prostředí Windows Runtime.

PassArray používá, když volající předá pole na metodu. Vstupní parametr typu jazyka C++ je `const` [Platform::Array](../cppcx/platform-array-class.md)\<T >.

FillArray používá, když volající předá pole pro metodu tak, aby vyplnil. Vstupní parametr typu jazyka C++ je [: Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)\<T >.

ReceiveArray používá, když volající přijímá pole, který přiděluje metodu. V jazyce C + +/ CX může vrátit pole ve vrácené hodnotě jako pole ^ nebo ho můžete vrátit jako výstupní parametr jako typ pole ^ *.

## <a name="passarray-pattern"></a>Vzor PassArray

Když metoda neupravuje klientský kód předá metodě C++ pole, metoda přijímá pole jako const Array ^. Na úrovni binární rozhraní (ABI) aplikace Windows Runtime to se označuje jako PassArray. Následující příklad ukazuje, jak předat pole, která je přidělena v jazyce JavaScript, která načte z něj funkci jazyka C++.

[!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]

Následující fragment kódu ukazuje metodu C++:

[!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]

## <a name="receivearray-pattern"></a>Vzor ReceiveArray

Ve vzoru ReceiveArray klientský kód deklaruje pole a předá metodě, která přiděluje paměť pro něj a inicializuje ji. Vstupní parametr typu jazyka C++ je ukazatel na systému hat: `Array<T>^*`. Následující příklad ukazuje, jak deklarovat objekt typu pole v jazyce JavaScript a předat funkci jazyka C++, který přiděluje paměť, inicializuje prvky a vrátí ji do jazyka JavaScript. JavaScript zpracovává přiřazeného pole jako návratové hodnoty, ale funkce C++ zpracovává jako výstupní parametr.

[!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]

Následující fragment kódu ukazuje dva způsoby, jak implementovat metodu C++:

[!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]

## <a name="fill-arrays"></a>Vyplnění polí

Pokud chcete přidělit pole s volajícího a inicializovat ani upravit v volaný použití `WriteOnlyArray`. Následující příklad ukazuje, jak implementovat funkci jazyka C++, který používá `WriteOnlyArray` a jeho volání z jazyka JavaScript.

[!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]

Následující fragment kódu ukazuje, jak implementovat metodu C++:

[!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]

## <a name="array-conversions"></a>Převody polí

Tento příklad ukazuje způsob použití [Platform::Array](../cppcx/platform-array-class.md) k vytvoření jiných typů kolekcí:

[!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]

Následující příklad ukazuje, jak vytvořit [Platform::Array](../cppcx/platform-array-class.md) z C-style pole a vrátit ji z veřejné metody.

[!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]

## <a name="jagged-arrays"></a>Vícenásobná pole

Systém typů prostředí Windows Runtime nepodporuje konceptu Vícenásobná pole, takže nemůže používat `IVector<Platform::Array<T>>` jako návratovou hodnotu nebo metoda parametr veřejnou metodu. Vícenásobné pole nebo sekvence sekvencí předejte ABI, použijte `IVector<IVector<T>^>`.

## <a name="use-arrayreference-to-avoid-copying-data"></a>Vyhněte se kopírování dat pomocí ArrayReference

V některých scénářích, kde je data předávána napříč ABI do [Platform::Array](../cppcx/platform-array-class.md)a nakonec chcete zpracovávat data v poli ve stylu jazyka C pro účinnost mezi body, můžete použít [Platform::arrayreference –](../cppcx/platform-arrayreference-class.md) Chcete-li se vyhnout operaci kopírování navíc. Při předání [Platform::arrayreference –](../cppcx/platform-arrayreference-class.md) jako argument pro parametr, který přijímá `Platform::Array`, `ArrayReference` se uloží data přímo do pole stylu C, který zadáte. Právě mějte na paměti, který `ArrayReference` nemá žádný zámek na zdrojová data tak, že data se změnily nebo odstranily v jiném vlákně, před dokončením volání, výsledky bude definováno.

Následující fragment kódu ukazuje, jak kopírovat výsledky [DataReader](/uwp/api/Windows.Storage.Streams.DataReader) operace do `Platform::Array` (vzorce) a potom nahraďte `ArrayReference` ke zkopírování dat přímo do pole stylu C:

[!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]

## <a name="avoid-exposing-an-array-as-a-property"></a>Vyhněte se úniku pole jako vlastnost

Obecně byste se měli vyhnout vystavení `Platform::Array` typu jako vlastnost v třídy ref class, protože celého pole se vrátí i v případě, že kód klienta je pouze pokusu o přístup k jeden element. Když budete chtít pořadí kontejner zveřejnit jako vlastnost v public ref class, [Windows::Foundation::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) je lepší volbou. V privátní nebo interní rozhraní API (které nejsou publikovány na metadata), zvažte použití standardní C++ kontejneru jako například [std::vector](../standard-library/vector-class.md).

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)
