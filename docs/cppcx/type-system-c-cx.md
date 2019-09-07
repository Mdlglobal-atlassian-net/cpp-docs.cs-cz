---
title: Systém typů (C++/CX)
ms.date: 02/03/2017
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
ms.openlocfilehash: bc45a835e37ff4e3ea239d253078bf50eab1b2ff
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740904"
---
# <a name="type-system-ccx"></a>Systém typů (C++/CX)

Pomocí architektury prostředí Windows Runtime můžete k psaní aplikací a komponent C++, které mají přímý přístup C# k rozhraní Windows API a spolupráci s ostatními prostředí Windows Runtime aplikacemi a komponentami, používat nástroje/CX, Visual Basic, Visual and JavaScript. Univerzální platforma Windows aplikace, které jsou napsány v C++ kompilaci do nativního kódu, který se spouští přímo v procesoru. Univerzální platforma Windows aplikace, které jsou napsány v C# nebo Visual Basic kompilovány do jazyka MSIL (Microsoft Intermediate Language) a spouštěny v modulu CLR (Common Language Runtime). Univerzální platforma Windows aplikace, které jsou napsané v JavaScriptu, se spustí v běhovém prostředí. Součásti operačního systému prostředí Windows Runtime samotné jsou napsány C++ v rámci a spouštěny jako nativní kód. Všechny tyto komponenty a aplikace Univerzální platforma Windows komunikují přímo prostřednictvím binárního rozhraní aplikace prostředí Windows Runtime (ABI).

Aby bylo možné povolit podporu prostředí Windows Runtime v moderních C++ idiom, společnost Microsoft vytvořila C++/CX. C++/CX poskytuje integrované základní typy a implementace základních prostředí Windows Runtime typů, které umožňují C++ aplikacím a komponentám komunikovat přes ABI pomocí aplikací, které jsou napsané v jiných jazycích. Můžete využívat libovolný typ prostředí Windows Runtime nebo vytvořit třídy, struktury, rozhraní a další uživatelsky definované typy, které mohou být spotřebovány jinými Univerzální platforma Windows aplikacemi a komponentami. Univerzální platforma Windows aplikace napsaná v C++sadě/CX může také používat regulární C++ třídy a struktury, pokud nemají veřejné přístupnost.

Podrobné informace o projekci jazyka C++/CX a o tom, jak funguje v rámci pokrývání, najdete v těchto blogových příspěvcích:

1. [C++/CX – část 0 \[z\]n: Úvod](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)

1. [C++/CX – část 1 \[z\]n: Jednoduchá třída](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)

1. [C++/CX – část 2 \[z\]n: Typy, které nosit Hats](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)

1. [C++/CX – část 3 \[z\]n: Pod konstrukcí](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)

1. [C++/CX – část 4 \[z\]n: Statické členské funkce](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)

## <a name="windows-metadata-winmd-files"></a>Soubory metadat Windows (. winmd)

Při kompilaci Univerzální platforma Windows aplikace, která je napsána C++v nástroji, kompilátor vygeneruje spustitelný soubor v nativním strojovém kódu a také vygeneruje samostatný soubor metadat Windows (. winmd), který obsahuje popisy veřejné prostředí Windows Runtime typy, které zahrnují třídy, struktury, výčty, rozhraní, Parametrizovaná rozhraní a delegáty. Formát metadat se podobá formátu, který se používá v .NET Framework sestaveních.  V C++ komponentě obsahuje soubor. winmd pouze metadata; spustitelný kód se nachází v samostatném souboru. V tomto případě prostředí Windows Runtime součásti, které jsou součástí systému Windows. Název souboru WinMD musí odpovídat nebo být prefixem kořenového oboru názvů ve zdrojovém kódu. (Pro .NET Framework jazyky obsahuje soubor. winmd jak kód, tak metadata, stejně jako sestavení .NET Framework.)

Metadata v souboru winmd představují publikovaný povrch kódu. Publikované typy jsou viditelné pro jiné platformy pro univerzální platformu Windows bez ohledu na to, v jakém jazyce jsou tyto jiné aplikace napsané. Proto metadata nebo publikovaný kód mohou obsahovat pouze typy určené systémem typu prostředí Windows Runtime. Jazykové konstrukce, které jsou specifické pro C++, například regulární třídy, pole, šablony nebo kontejnery STL, nelze publikovat v metadatech, protože JavaScript nebo C# klientská aplikace by nevěděly, co s nimi dělat.

Zda je typ nebo metoda viditelná v metadatech, závisí na tom, jaké Modifikátory dostupnosti jsou pro něj použity. Aby bylo možné zobrazit typ, musí být deklarován v oboru názvů a musí být deklarován jako Public. Neveřejná referenční třída je povolena jako interní typ pomocné rutiny v kódu; v metadatech se jen nezobrazí. I ve veřejné referenční třídě nejsou všechny členy nutně viditelné. V následující tabulce je uveden vztah mezi C++ specifikátory přístupu ve veřejné referenční třídě a prostředí Windows Runtime viditelnost metadat:

|||
|-|-|
|**Publikováno v metadatech**|**Nepublikováno v metadatech**|
|public|private|
|protected|internal|
|chráněno jako veřejné|private protected|

Můžete použít **Prohlížeč objektů** k zobrazení obsahu souborů. winmd. Prostředí Windows Runtime součásti, které jsou součástí systému Windows, jsou v souboru Windows. winmd. Výchozí soubor. winmd obsahuje základní typy, které se používají v C++/CX, a Platform. winmd obsahuje další typy z oboru názvů platformy. Ve výchozím nastavení jsou tyto tři soubory. winmd zahrnuty do každého C++ projektu aplikace Univerzální platforma Windows.

> [!TIP]
> Typy v [oboru názvů Platform:: Collections](../cppcx/platform-collections-namespace.md) se nezobrazí v souboru WinMD, protože nejsou veřejné. Jsou C++to specifické implementace rozhraní, které jsou definovány v `Windows::Foundation::Collections`. Prostředí Windows Runtime aplikace, která je napsána v C# jazyce JavaScript nebo neví, co je [Třída Platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md) , ale `Windows::Foundation::Collections::IVector`může spotřebovat. `Platform::Collections` Typy jsou definovány v Collection. h.

## <a name="windows-runtime-type-system-in-ccx"></a>Systém typů prostředí Windows Runtime v C++/CX

Následující části popisují hlavní funkce systému prostředí Windows Runtime typů a jejich podporu v C++/CX.

### <a name="namespaces"></a>Jmenné prostory

Všechny typy prostředí Windows Runtime musí být deklarovány v rámci oboru názvů; rozhraní API systému Windows je samoně Uspořádáno podle oborů názvů. Soubor. winmd musí mít stejný název, který má kořenový obor názvů. Například třída s názvem A. B. C. MyClass může být vytvořena pouze v případě, že je definována v souboru metadat s názvem A. winmd nebo A. B. winmd nebo A. B. C. winmd. Název knihovny DLL není nutné odpovídat názvu souboru. winmd.

Rozhraní API systému Windows samotné bylo Reinvented jako knihovna tříd, která je uspořádána podle oborů názvů.  Všechny součásti prostředí Windows Runtime jsou deklarovány v oborech názvů Windows. *.

Další informace naleznete v části [obory názvů a viditelnost typů](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="fundamental-types"></a>Základní typy

Prostředí Windows Runtime definuje následující základní typy, UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, Double, Char16, Boolean a String. C++/CX podporuje základní číselné typy ve svém výchozím oboru názvů jako UInt16, UInt32, UInt64, Int16, Int32, Int64, float32, float64 a Char16. Logická hodnota a řetězec jsou také definovány v oboru názvů platformy.

C++/CX také definuje uint8, který je `unsigned char`ekvivalentní k, což není v prostředí Windows Runtime podporováno a nelze ho použít ve veřejných rozhraních API.

Základní typ může mít hodnotu null, protože ho zabalíte v rozhraní rozhraní [Platform:: iBox](../cppcx/platform-ibox-interface.md) . Další informace naleznete v tématu [třídy a struktury hodnot](../cppcx/value-classes-and-structs-c-cx.md).

Další informace o základních typech najdete v tématu [základní typy](../cppcx/fundamental-types-c-cx.md) .

### <a name="strings"></a>Řetězce

Prostředí Windows Runtime řetězec je neproměnlivá sekvence 16bitových znaků UNICODE. Prostředí Windows Runtime řetězec je projekt jako `Platform::String^`. Tato třída poskytuje metody pro vytváření řetězců, manipulaci a převod na a z `wchar_t`.

Další informace najdete v tématu [řetězce](../cppcx/strings-c-cx.md).

### <a name="arrays"></a>Pole

Prostředí Windows Runtime podporuje jednorozměrné pole libovolného typu. Pole polí nejsou podporována.  V C++/CX prostředí Windows Runtime pole jsou považována za [třídu Platform:: Array](../cppcx/platform-array-class.md).

Další informace najdete v tématech [Array a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md) .

### <a name="ref-classes-and-structs"></a>Referenční třídy a struktury

Prostředí Windows Runtime třída je probíhají v C++/CX jako ref class nebo ref struct, protože jsou zkopírovány odkazem. Správa paměti pro referenční třídy a struktury ref jsou transparentně zpracovávány prostřednictvím počítání odkazů. Když se poslední odkaz na objekt přestane vyřadit z rozsahu, objekt je zničen. Struktura ref class nebo ref může:

- Obsahují jako členy konstruktory, metody, vlastnosti a události. Tito členové mohou mít veřejné, privátní, chráněné nebo interní přístupnost.

- Může obsahovat definice privátního vnořeného výčtu, struktury nebo třídy.

- Může přímo dědit z jedné základní třídy a může implementovat libovolný počet rozhraní. Všechny třídy ref jsou implicitně převoditelné na [třídu Platform:: Object](../cppcx/platform-object-class.md) a mohou přepsat své virtuální metody, například [Object:: ToString](../cppcx/platform-object-class.md#tostring).

Třída ref class, která má veřejný konstruktor, musí být deklarována jako zapečetěná, aby se zabránilo dalšímu odvození.

Další informace naleznete v tématu [ref Classes and Structs](../cppcx/ref-classes-and-structs-c-cx.md)

### <a name="value-classes-and-structs"></a>Hodnotové třídy a struktury

Struktura hodnot nebo hodnot představuje základní strukturu dat a obsahuje pouze pole, která mohou být třídy hodnot, struktury hodnot nebo typ `Platform::String^`.  Struktury hodnot a třídy hodnot se zkopírují podle hodnoty.

Pomocí zabalení v rozhraní IBox může být vytvořena struktura hodnot s možnou hodnotou null.

Další informace naleznete v tématu [třídy a struktury hodnot](../cppcx/value-classes-and-structs-c-cx.md).

### <a name="partial-classes"></a>Dílčí třídy

Funkce částečné třídy umožňuje definovat jednu třídu v rámci více souborů. Používá se hlavně pro povolení nástrojů pro generování kódu, jako je Editor XAML, pro úpravu jednoho souboru bez zásahu do souboru, který upravujete.

Další informace naleznete v tématu [Partial Classes](../cppcx/partial-classes-c-cx.md) .

### <a name="properties"></a>Vlastnosti

Vlastnost je veřejný datový člen libovolného prostředí Windows Runtimeho typu a je implementován jako dvojice metod get/set. Klientský kód přistupuje k vlastnosti, jako by se jednalo o veřejné pole. Vlastnost, která nevyžaduje žádný vlastní kód Get nebo set, je známá jako *triviální vlastnost* a lze ji deklarovat bez explicitních metod Get nebo set.

Další informace najdete v tématu [vlastnosti](../cppcx/properties-c-cx.md).

### <a name="windows-runtime-collections-in-ccx"></a>Kolekce prostředí Windows Runtime v C++/CX

Prostředí Windows Runtime definuje sadu rozhraní pro typy kolekce, které jednotlivé jazyky implementují vlastním způsobem. C++/CX poskytuje implementace ve třídě [Platform:: Collections:: Vector](../cppcx/platform-collections-vector-class.md), [Platform:: Collections:: map](../cppcx/platform-collections-map-class.md)a dalších souvisejících typech konkrétní kolekce, které jsou kompatibilní se svými protějšky Standard Template Library (STL).

Další informace najdete v tématu [kolekce](../cppcx/collections-c-cx.md).

### <a name="template-ref-classes"></a>Šablony referenčních tříd

Soukromé a interní referenční třídy mohou být šablony a specializované.

Další informace naleznete v tématu [template ref classs](../cppcx/template-ref-classes-c-cx.md).

### <a name="interfaces"></a>Rozhraní

Rozhraní prostředí Windows Runtime definuje sadu veřejných vlastností, metod a událostí, které musí být implementovány pomocí referenční třídy nebo struktury ref, pokud dědí z rozhraní.

Další informace naleznete v tématu [rozhraní](../cppcx/interfaces-c-cx.md).

### <a name="enums"></a>Výčty

Třída výčtu v prostředí Windows Runtime je podobná výčtu v C++oboru. Základní typ je Int32, pokud atribut [Flags] není použit – v takovém případě je nadřízený typ UInt32.

Další informace naleznete v tématu [výčty](../cppcx/enums-c-cx.md).

### <a name="delegates"></a>Delegáty

Delegát v prostředí Windows Runtime je podobný objektu std:: Function v C++. Jedná se o speciální druh referenční třídy, který se používá k vyvolání funkcí poskytovaných klientem, které mají kompatibilní signatury.  Delegáti jsou nejčastěji používány v prostředí Windows Runtime jako typ události.

Další informace najdete v tématu [Delegáti](../cppcx/delegates-c-cx.md).

### <a name="exceptions"></a>Výjimky

V C++/CX můžete zachytit typy vlastních výjimek, [std:: Exception](../standard-library/exception-class.md) Types a [Platform:: Exception](../cppcx/platform-exception-class.md) Types.

Další informace najdete v tématu [výjimky](../cppcx/exceptions-c-cx.md).

### <a name="events"></a>Události

Událost je veřejný člen v referenční třídě nebo struktuře ref, jejichž typ je typ delegáta. Událost lze vyvolat pouze v případě, že je aktivována, pomocí vlastnící třídy. Nicméně klientský kód může poskytnout své vlastní funkce, které jsou známé jako obslužné rutiny událostí a jsou vyvolány, pokud vlastnící třída událost vyvolá.

Další informace najdete v tématu [události](../cppcx/events-c-cx.md).

### <a name="casting"></a>Přetypování

C++/CX podporuje operátory C++ přetypování [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md)a [reinterpret_cast](../cpp/reinterpret-cast-operator.md)a také **safe_cast** operátor, který je specifický pro C++/CX.

Další informace naleznete v tématu [přetypování](../cppcx/casting-c-cx.md).

### <a name="boxing"></a>Zabalení

Zabalená proměnná je typ hodnoty, která je zabalena v typu odkazu v situacích, kde jsou požadovány sémantiky odkazů.

Další informace naleznete v tématu [zabalení](../cppcx/boxing-c-cx.md).

### <a name="attributes"></a>Atributy

Atribut je hodnota metadat, která může být použita na libovolný typ prostředí Windows Runtime nebo člen typu a lze ji zkontrolovat v době běhu. Prostředí Windows Runtime definuje sadu běžných atributů v `Windows::Foundation::Metadata` oboru názvů. Uživatelsky definované atributy ve veřejných rozhraních nejsou v této verzi prostředí Windows Runtime podporovány.

## <a name="api-deprecation"></a>Zastaralé rozhraní API

Popisuje, jak označit veřejná rozhraní API jako zastaralá pomocí stejného atributu, který používá typy prostředí Windows Runtime systému.

Další informace naleznete v tématu [zastaralé typy a členy](../cppcx/deprecating-types-and-members-c-cx.md).

## <a name="see-also"></a>Viz také:

[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
