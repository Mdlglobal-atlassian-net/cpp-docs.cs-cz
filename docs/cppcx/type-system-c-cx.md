---
title: Systém typů (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7b9f17007c1614761f1b7872d8d421f0f5e18df
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105169"
---
# <a name="type-system-ccx"></a>Systém typů (C + +/ CX)

Pomocí architektury Windows Runtime, můžete pomocí jazyka C + +/ CX, Visual Basic, Visual C# a JavaScript pro zápis aplikace a komponenty, které přímo přístup k rozhraní API Windows a zajistit vzájemnou funkční spolupráci s ostatními modulu Windows Runtime aplikace a komponenty. Aplikace pro univerzální platformu Windows, které jsou napsané v jazyce C++ se kompilují do nativního kódu, který se spustí přímo v procesoru. Aplikace pro univerzální platformu Windows, které jsou napsány v jazyce C# nebo Visual Basic zkompilovat pro jazyk Microsoft intermediate language (MSIL) a spustit v modulu common language runtime (CLR). Aplikace pro univerzální platformu Windows, které jsou napsané v jazyce JavaScript spouštění v prostředí za běhu. Součásti operačního systému Windows Runtime, samotné jsou napsané v jazyce C++ a spouštět v nativním kódu. Všechny tyto součásti a aplikace pro univerzální platformu Windows komunikovat přímo pomocí prostředí Windows Runtime binárním rozhraním aplikace (ABI).

Pokud chcete povolit podporu pro prostředí Windows Runtime v moderní C++ idiom, společnost Microsoft vytvořila C + +/ CX. C + +/ CX poskytuje základní typy a implementace základní typy modulu Windows Runtime, které umožňují aplikací v jazyce C++ a komponenty pro komunikaci mezi ABI s aplikacemi, které jsou napsané v jiných jazycích. Můžete používat jakýkoli typ Windows Runtime nebo vytvořit třídy, struktury, rozhraní a další uživatelem definované typy, které mohou být spotřebovány jiných aplikací pro univerzální platformu Windows a komponenty. aplikace univerzální platformy Windows, která je napsána v jazyce C + +/ CX můžete také použít regulární C++ třídy a struktury tak dlouho, dokud nebudou mít přístupnost public.

Podrobné informace o jazyce C + +/ CX jazyk projekce a jak to funguje pod pokličkou, najdete v těchto příspěvcích blogu:

1. [C + +/ CX součástí 0 \[n\]: Úvod](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)

1. [C + +/ CX, část 1 ze \[n\]: jednoduchou třídu](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)

1. [C + +/ CX část 2 \[n\]: typy, které Wear Hats](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)

1. [C + +/ CX část 3 \[n\]: vytvářený](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)

1. [C + +/ CX část 4 \[n\]: statické členské funkce](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)

## <a name="windows-metadata-winmd-files"></a>Soubory metadat (.winmd) pro Windows

Při kompilaci aplikace univerzální platformu Windows, která je napsána v jazyce C++, kompilátor vygeneruje spustitelný soubor do nativního strojového kódu a také vytváří samostatný soubor metadat (.winmd) Windows, který obsahuje popisy veřejné typy Windows Runtime které obsahují třídy, struktury, výčty, rozhraní, parametrizované rozhraní a delegátů. Formát metadat vypadá podobně jako na formát, který se používá v sestavení rozhraní .NET Framework.  V komponentě C++ soubor winmd obsahuje pouze metadata; spustitelný kód je umístěn v samostatném souboru. To platí pro součásti prostředí Windows Runtime, které jsou součástí Windows. Název souboru WinMD musí odpovídat nebo se předponu kořenového oboru názvů ve zdrojovém kódu. (Pro jazyky rozhraní .NET Framework, soubor .winmd obsahuje kód a metadata, stejně jako na sestavení rozhraní .NET Framework.)

Metadata v souboru .winmd představuje publikované ploše typu kódu. Publikované typy jsou viditelné pro ostatní univerzální platformy Windows bez ohledu na to, jaký jazyk jsou tyto aplikace napsané v. Proto se metadata nebo publikované kódu, může obsahovat pouze typy určené systém typů prostředí Windows Runtime. Konstrukce jazyka, které jsou specifické pro C++, jako jsou pravidelné třídy, pole, šablony nebo kontejnery STL, nelze v metadatech publikovat, protože klientské aplikace Javascript nebo C# nebude vědět, co dělat s nimi.

Určuje, zda je viditelný v metadatech typu nebo metodě závisí na jaké modifikátory se použijí k němu. Aby bylo vidět, typ musí být deklarovány v oboru názvů a musí být deklarován jako veřejná. Neveřejné referenční třídy je povolený jako typ interní pomocné rutiny ve vašem kódu; právě nejsou viditelná v metadatech. Všichni členové jsou i v public ref class, nemusí být viditelná. V následující tabulce jsou uvedeny vztah mezi specifikátory přístupu jazyka C++ v třída public ref class a viditelnost metadat prostředí Windows Runtime:

|||
|-|-|
|**Publikování metadat**|**Nezveřejněno v metadatech**|
|public|private|
|protected|internal|
|veřejné, chráněné|privátní, chráněné|

Můžete použít **prohlížeče objektů** zobrazíte obsah soubory .winmd. Součásti prostředí Windows Runtime, které jsou součástí Windows jsou v souboru Windows.winmd. Default.winmd soubor obsahuje základní typy, které se používají v jazyce C + +/ CX a platform.winmd obsahuje další typy z oboru názvů Platform. Ve výchozím nastavení jsou zahrnuty tyto tři soubory winmd v každém projektu C++ pro aplikace univerzální platformy Windows.

> [!TIP]
> Typy v [Platform::Collections – Namespace](../cppcx/platform-collections-namespace.md) nejsou zobrazeny v souboru winmd, protože nejsou veřejné. Jsou privátní implementace specifické pro C++, které jsou definovány v rozhraní `Windows::Foundation::Collections`. Aplikace s Windows Runtime, která je napsána v jazyce JavaScript nebo C# neví, co [Platform::Collections:: Vector – třída](../cppcx/platform-collections-vector-class.md) je, ale může spotřebovávat `Windows::Foundation::Collections::IVector`. `Platform::Collections` Typy jsou definovány v collection.h.

## <a name="windows-runtime-type-system-in-ccx"></a>Systém typů prostředí Windows Runtime v jazyce C + +/ CX

Následující části popisují hlavní funkce systému typů modulu Windows Runtime a jak jsou podporovány v jazyce C + +/ CX.

### <a name="namespaces"></a>Jmenné prostory

Všechny typy modulu Windows Runtime musí být deklarovány v oboru názvů; samotné rozhraní API Windows je uspořádaný podle oborů názvů. Soubor .winmd musí mít stejný název, který má kořenový obor názvů. Například třída, která má název A.B.C.MyClass dá vytvořit instance pouze v případě, že je definována v souboru metadat, který je pojmenován A.winmd a A.B.winmd nebo A.B.C.winmd. Název knihovny DLL nemusí odpovídat názvu souboru .winmd.

Samotné rozhraní API Windows má byla přepracovaná jako knihovna skvěle třída, která je seřazená podle oborů názvů.  Všechny součásti modulu Windows Runtime jsou deklarovány v oborech názvů Windows.*.

Další informace najdete v tématu [obory názvů a viditelnost typů](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="fundamental-types"></a>Základní typy

Modul Windows Runtime definuje následující základní typy, UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, jedním, Double, Char16, logická hodnota a řetězec. C + +/ CX podporuje základní číselné typy jako typ uint16, uint32, uint64, int16, int32, int64, float32, float64 a char16 v její výchozí obor názvů. Datový typ Boolean a řetězce je definována v oboru názvů Platform.

C + +/ CX také definuje uint8 ekvivalentní `unsigned char`, což není podporováno v modulu Windows Runtime a nelze použít ve veřejných rozhraní API.

Základní typ se dají vytvořit s možnou hodnotou Null v obalením [Platform::ibox – rozhraní](../cppcx/platform-ibox-interface.md) rozhraní. Další informace najdete v tématu [hodnotové třídy a struktury](../cppcx/value-classes-and-structs-c-cx.md).

Další informace o základních typů, najdete v části [základní typy](../cppcx/fundamental-types-c-cx.md)

### <a name="strings"></a>Řetězce

Řetězec modulu Windows Runtime je neměnný posloupnost znaků UNICODE 16 bitů. Řetězec modulu Windows Runtime je promítat jako `Platform::String^`. Tato třída poskytuje metody pro vytváření řetězce, manipulaci a převodu do a z `wchar_t`.

Další informace najdete v tématu [řetězce](../cppcx/strings-c-cx.md).

### <a name="arrays"></a>Pole

Modul Windows Runtime podporuje 1rozměrné pole libovolného typu. Pole polí se nepodporují.  V jazyce C + +/ CX, pole prostředí Windows Runtime se vykreslují jako [Platform::Array – třída](../cppcx/platform-array-class.md).

Další informace najdete v tématu [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)

### <a name="ref-classes-and-structs"></a>Referenční třídy a struktury

Třída Windows Runtime je plánované v jazyce C + +/ CX jako ref class nebo ref struct, protože se zkopírují podle odkazu. Správa paměti pro referenční třídy a struktury ref se transparentně zpracovává prostřednictvím počítání odkazů. Při poslední odkaz na objekt dostane mimo rozsah, bude objekt zničen. Třída nebo "REF" struktury ref provádět následující akce:

- Obsahovat jako konstruktory členů, metody, vlastnosti a události. Tyto členy mohou mít veřejný, privátní, chráněné nebo interní přístupnost.

- Může obsahovat privátní vnořené výčtu, struktury nebo třídy definice.

- Může dědit přímo z jedné základní třídy a může implementovat libovolný počet rozhraní. Všechny referenční třídy jsou implicitně převoditelné [Platform::Object – třída](../cppcx/platform-object-class.md) a může přepsat virtuální metody – například [Object::ToString](../cppcx/platform-object-class.md#tostring).

Ref class, která má veřejný konstruktor musí být deklarován jako zapečetěný, aby se zabránilo dalším odvození.

Další informace najdete v tématu [referenční třídy a struktury](../cppcx/ref-classes-and-structs-c-cx.md)

### <a name="value-classes-and-structs"></a>Hodnota třídy a struktury

Hodnota třídy nebo struktury hodnota představuje základní datová struktura a obsahuje pouze pole, které mohou být hodnota třídy, struktury hodnotu nebo typ `Platform::String^`.  Hodnota strukturám a třídám hodnotu zkopírují podle hodnoty.

Struktura hodnotu je možné provádět s možnou hodnotou Null pomocí zabalení IBox rozhraní.

Další informace najdete v tématu [hodnotové třídy a struktury](../cppcx/value-classes-and-structs-c-cx.md).

### <a name="partial-classes"></a>Částečné třídy

Částečné třídy funkce umožňuje jednu třídu k definované ve více souborech. Používá se především pro povolení generování kódu nástroje, jako je XAML editor k úpravě souborů bez zásahu do souboru, který můžete upravit.

Další informace najdete v tématu [částečné třídy](../cppcx/partial-classes-c-cx.md)

### <a name="properties"></a>Vlastnosti

Vlastnost je členem veřejné datové libovolný typ Windows Runtime a je implementovaný jako dvojice metody get/set. Klientský kód přistupuje k vlastnosti, jako by šlo veřejné pole. Získat vlastnosti, která vyžaduje žádné vlastní nebo sadu kód se označuje jako *triviální vlastnost* a můžete deklarované bez explicitních get nebo set metod.

Další informace najdete v tématu [vlastnosti](../cppcx/properties-c-cx.md).

### <a name="windows-runtime-collections-in-ccx"></a>Kolekce modulu Windows Runtime v jazyce C + +/ CX

Modul Windows Runtime definuje sadu rozhraní pro typy kolekcí, které implementují jednotlivé jazyky vlastním způsobem. C + +/ CX poskytuje implementaci v [Platform::Collections:: Vector – třída](../cppcx/platform-collections-vector-class.md), [Platform::Collections:: map – třída](../cppcx/platform-collections-map-class.md)a další související konkrétní kolekci typů, které jsou kompatibilní s jejich Standardní knihovny šablon (STL) protějšky.

Další informace najdete v tématu [kolekce](../cppcx/collections-c-cx.md).

### <a name="template-ref-classes"></a>Šablony referenčních tříd

Privátní a interní referenční třídy může být bez vizuálního vzhledu a specializované.

Další informace najdete v tématu [šablony referenčních tříd](../cppcx/template-ref-classes-c-cx.md).

### <a name="interfaces"></a>Rozhraní

Rozhraní Windows Runtime definuje sadu veřejné vlastnosti, metody a události, které musí implementovat třídy ref class nebo ref struct, pokud se dědí z rozhraní.

Další informace najdete v tématu [rozhraní](../cppcx/interfaces-c-cx.md).

### <a name="enums"></a>Výčty

Rozsah výčtu v jazyce C++ se podobá výčet tříd v prostředí Windows Runtime. Základní typ je typ int32, pokud je použit atribut [Flags] – v takovém případě je základní typ uint32.

Další informace najdete v tématu [výčty](../cppcx/enums-c-cx.md).

### <a name="delegates"></a>Delegáty

Delegát v modulu Windows Runtime je analogická objektu std::function v jazyce C++. Je zvláštním druhem třídy ref class, který se použije k vyvolání funkce poskytované klienta, které mají kompatibilní signatury.  Delegáty se běžně používají v modulu Windows Runtime jako typ události.

Další informace najdete v tématu [delegáti](../cppcx/delegates-c-cx.md).

### <a name="exceptions"></a>Výjimky

V jazyce C + +/ CX, můžete zachytit vlastní typy výjimek, [std::exception](../standard-library/exception-class.md) typů, a [Platform::Exception](../cppcx/platform-exception-class.md) typy.

Další informace najdete v tématu [výjimky](../cppcx/exceptions-c-cx.md).

### <a name="events"></a>Události

Událost je členem veřejné třídy ref class nebo ref struct, jehož typ je typ delegátu. Událost může být volána pouze – to znamená, aktivuje – vlastnící třídou. Kód klienta ale můžete zadat vlastní funkce, které jsou označovány jako obslužné rutiny událostí a jsou vyvolány při vlastnící třída vyvolá událost.

Další informace najdete v tématu [události](../cppcx/events-c-cx.md).

### <a name="casting"></a>Přetypování

C + +/ CX podporuje standardní operátorů přetypování jazyka C++ [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md), a [reinterpret_cast](../cpp/reinterpret-cast-operator.md)a také **safe_cast**operátor, který je specifická pro C + +/ CX.

Další informace najdete v tématu [přetypování](../cppcx/casting-c-cx.md).

### <a name="boxing"></a>Zabalení

Pevně určené proměnnou je typ hodnoty, která je zabalena v typu odkazu v situacích, kde se vyžadují odkazové sémantiky.

Další informace najdete v tématu [zabalení](../cppcx/boxing-c-cx.md).

### <a name="attributes"></a>Atributy

Atribut je hodnota metadat, která můžete použít pro libovolný typ Windows Runtime nebo člen typu a lze ho možné zkontrolovat v době běhu. Definuje sadu společné atributy v prostředí Windows Runtime `Windows::Foundation::Metadata` oboru názvů. Uživatelsky definované atributy u veřejných rozhraní nepodporuje modul Windows Runtime v této verzi.

## <a name="api-deprecation"></a>Zastarání rozhraní API

Popisuje, jak označit veřejných rozhraní API jako zastaralé pomocí stejný atribut, který používá systém typy Windows Runtime.

Další informace najdete v tématu [vyřazování typů a členů](../cppcx/deprecating-types-and-members-c-cx.md).

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)
