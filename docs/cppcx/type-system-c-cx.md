---
title: Systém typů (C + +/ CX) | Microsoft Docs
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0a1016836d44b8ee83b033bf2d542d4e9b1db413
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="type-system-ccx"></a>Systém typů (C + +/ CX)
Pomocí prostředí Windows Runtime architektury, můžete pomocí C + +/ CX, Visual Basic, Visual C# a JavaScript pro zápis aplikace a součásti, které přímo přístup k rozhraní API systému Windows a zajistit vzájemnou funkční spolupráci s jinými aplikace Windows Runtime a součásti. Univerzální aplikace platformy Windows, které jsou napsané v jazyce C++ kompilace nativního kódu, které provádí přímo v procesoru. Univerzální platforma Windows aplikace, které jsou napsané v C# nebo Visual Basic zkompilovat do převodního jazyka Microsoft (MSIL) a spustit v common language runtime (CLR). Univerzální aplikace platformy Windows, které jsou napsané v jazyce JavaScript spustit v prostředí runtime. Sami součásti operačního systému Windows Runtime jsou napsané v jazyce C++ a spouštět v nativním kódu. Všechny tyto součásti a Universal Windows Platform apps komunikovat přímo přes rozhraní binární aplikace Windows Runtime (ABI).  
  
 Společnost Microsoft vytvořila povolení podpory pro prostředí Windows Runtime v moderní stylu C++, C + +/ CX. C + +/ CX poskytuje integrované základní typy a implementace základní typy prostředí Windows Runtime, které umožňují C++ aplikace a součásti, které komunikují přes ABI s aplikacemi, které jsou zapsány v dalších jazycích. Můžete využívat žádný typ, prostředí Windows Runtime nebo vytvoření třídy, struktury, rozhraní a další uživatelem definované typy, které mohou být spotřebovávána jiné aplikace pro univerzální platformu Windows a součásti. aplikaci pro univerzální platformu Windows, která je napsán v jazyce C + +/ CX můžete také použít regulární C++ třídy a struktury tak dlouho, dokud nemají veřejnou dostupnost.  
  
 Pro podrobné informace o jazyce C + +/ CX jazyk projekce a jak to funguje v pozadí, najdete v těchto příspěvcích na blogu:  
  
1.  [C + +/ CX část 0 \[n\]: Úvod](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)  
  
2.  [C + +/ CX část 1 / \[n\]: jednoduchý – třída](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)  
  
3.  [C + +/ CX část 2 / \[n\]: typy, které nosit klobouky](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)  
  
4.  [C + +/ CX části 3 \[n\]: v části vytváření](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)  
  
5.  [C + +/ CX část 4 \[n\]: statické členské funkce](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)  
  
## <a name="windows-metadata-winmd-files"></a>Soubory metadat (.winmd) Windows  
 Při kompilaci aplikace univerzální platformu Windows, který je napsán v jazyce C++ kompilátor generuje spustitelný soubor v nativním kódu počítače a také vytváří samostatný soubor metadat (.winmd) systému Windows, který obsahuje popisy veřejné typy prostředí Windows Runtime která zahrnuje třídy, struktury, výčty, rozhraní, parametrizované rozhraní a delegáti. Formát metadat se podobá formátu, který se používá v sestavení rozhraní .NET Framework.  V komponentě C++ .winmd soubor obsahuje pouze metadata; Kód spustitelný soubor se nachází v samostatném souboru. To platí pro prostředí Windows Runtime součásti, které jsou součástí systému Windows. Název souboru WinMD musí odpovídat nebo předponu kořenového oboru názvů ve zdrojovém kódu. (Pro jazyky rozhraní .NET Framework, .winmd soubor obsahuje kód a metadata, stejně jako sestavení rozhraní .NET Framework.)  
  
 Metadata v souboru .winmd představuje publikované prostor vašeho kódu. Typy publikovaných budou viditelné i pro jiné platformy Universal Windows bez ohledu na to, v jakém jazyce na jiné aplikace, které jsou napsané v. Proto metadata nebo publikované kódu, může obsahovat pouze typy určeného systém typů prostředí Windows Runtime. Jazykové konstrukty, které jsou specifické pro C++, jako je například regulární třídy pole, šablony nebo kontejnery STL, nelze publikovat v metadatech, protože klientské aplikace Javascript nebo C# vědět, co dělat s nimi.  
  
 Zda je viditelný v metadatech typ nebo metoda závisí na jaké modifikátory usnadnění přístupu se použijí k němu. Chcete-li být viditelné, typu musí být deklarován v oboru názvů a musí být deklarován jako veřejné. Třída neveřejný ref je povoleno jako typ interní pomocné rutiny do vašeho kódu; právě nejsou viditelná v metadatech. Ne všechny členy jsou i v třídě veřejné ref nutně viditelné. Následující tabulka uvádí vztah mezi specifikátory přístupu C++ v třídě veřejné ref a viditelnost metadat prostředí Windows Runtime:  
  
|||  
|-|-|  
|**V metadatech publikovaný**|**V metadatech není publikovaný**|  
|public|private|  
|protected|internal|  
|veřejné chráněný|privátní chráněný|  
  
 Můžete použít **Prohlížeč objektů** zobrazíte obsah .winmd souborů. V souboru Windows.winmd se prostředí Windows Runtime součásti, které jsou součástí systému Windows. Soubor default.winmd obsahuje základní typy, které se používají v jazyce C + +/ CX a platform.winmd obsahuje další typy z oboru názvů Platform. Ve výchozím nastavení jsou tyto tři soubory .winmd zahrnuté ve všech projektech C++ pro aplikace pro univerzální platformu Windows.  
  
> [!TIP]
>  Typy v [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md) nezobrazí v souboru .winmd, protože nejsou veřejné. Jsou privátní C++ konkrétní implementace rozhraní, které jsou definovány v `Windows::Foundation::Collections`. Prostředí Windows Runtime aplikaci, která je napsán v jazyce JavaScript nebo C# nepodporuje vědět, co [Platform::Collections::Vector třída](../cppcx/platform-collections-vector-class.md) je, ale může využívat `Windows::Foundation::Collections::IVector`. `Platform::Collections` Typy jsou definované v collection.h.  
  
## <a name="windows-runtime-type-system-in-ccx"></a>Prostředí Windows Runtime systém typů v jazyce C + +/ CX  
 Následující části popisují hlavní funkce systém typů prostředí Windows Runtime a jak jsou podporovány v jazyce C + +/ CX.  
  
### <a name="namespaces"></a>Jmenné prostory  
 Všechny typy prostředí Windows Runtime musí být deklarován v oboru názvů; rozhraní API systému Windows, samotné je seřazená podle obory názvů. Soubor .winmd musí mít stejný název, který má kořenového oboru názvů. Například třídu, která je s názvem A.B.C.MyClass se dá vytvořit instance pouze v případě, že je definována v souboru metadat, který je pojmenován A.winmd nebo A.B.winmd nebo A.B.C.winmd. Název knihovny DLL nemusí odpovídat názvu souboru .winmd.  
  
 Rozhraní API systému Windows, samotné má byla reinvented jako knihovnu dobře započítané třída, která je seřazená podle obory názvů.  Všechny součásti prostředí Windows Runtime jsou deklarované v oborech názvů Windows.*.  
  
 Další informace najdete v tématu [obory názvů a viditelnost typů](../cppcx/namespaces-and-type-visibility-c-cx.md).  
  
### <a name="fundamental-types"></a>Základní typy  
 Prostředí Windows Runtime definuje následující základní typy, UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, Double, Char16, logická hodnota a řetězec. C + +/ CX podporuje základní číselnými typy v jeho výchozí obor názvů jako uint16, uint32, uint64, int16, int32, int64, float32, float64 a char16. Logická hodnota a řetězce je definována v oboru názvů Platform.  
  
 C + +/ CX také definuje uint8 ekvivalentní `unsigned char`, která není podporována v prostředí Windows Runtime a nelze ji použít v veřejná rozhraní API.  
  
 Základní typ může být provedené s možnou hodnotou Null v zabalení [Platform::IBox rozhraní](../cppcx/platform-ibox-interface.md) rozhraní. Další informace najdete v tématu [hodnota třídy a struktury](../cppcx/value-classes-and-structs-c-cx.md).  
  
 Další informace o základní typy najdete v tématu [základní typy](../cppcx/fundamental-types-c-cx.md)  
  
### <a name="strings"></a>Řetězce  
 Prostředí Windows Runtime řetězec je v neměnné sekvenci znaky UNICODE-16 bitů. Prostředí Windows Runtime řetězec se promítá jako `Platform::String^`. Tato třída poskytuje metody pro vytváření řetězce, manipulaci a převod na a z `wchar_t`.  
  
 Další informace najdete v tématu [řetězce](../cppcx/strings-c-cx.md).  
  
### <a name="arrays"></a>Pole  
 Prostředí Windows Runtime podporuje 1jednorozměrná pole libovolného typu. Pole pole nejsou podporována.  V jazyce C + +/ CX, jako jsou projektovat prostředí Windows Runtime pole [Platform::Array třída](../cppcx/platform-array-class.md).  
  
 Další informace najdete v tématu [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)  
  
### <a name="ref-classes-and-structs"></a>REF třídy a struktury  
 Prostředí Windows Runtime třídy se promítá v jazyce C + +/ CX jako ref třídě nebo struktuře ref, protože se kopírují odkazem. Správa paměti pro ref třídy a struktury ref transparentně zpracovává prostřednictvím počítání odkazů. Při poslední odkazem na objekt je mimo rozsah, objekt zničena. Ref – třída nebo ref struct můžete:  
  
-   Obsahovat jako členy konstruktory, metody, vlastnosti a události. Tito členové může mít usnadnění veřejné, privátní, chráněný nebo interní.  
  
-   Může obsahovat privátní vnořené výčtu, struktura nebo definice tříd.  
  
-   Přímo z jedné základní třídy lze dědit a můžete implementovat libovolný počet rozhraní. Všechny třídy ref jsou implicitně převést na [Platform::Object třída](../cppcx/platform-object-class.md) a můžete přepsat své virtuální metody – například [Object::ToString](../cppcx/platform-object-class.md#tostring).  
  
 Ref třídy, která má konstruktor public, který musí být deklarován jako zapečetěné, aby se zabránilo dalším odvození.  
  
 Další informace najdete v tématu [Ref třídy a struktury](../cppcx/ref-classes-and-structs-c-cx.md)  
  
### <a name="value-classes-and-structs"></a>Hodnota třídy a struktury  
 Hodnota třídě nebo struktuře hodnota reprezentuje strukturu, základní data a obsahuje pouze pole, které může být hodnota třídy, struktury hodnotu nebo typ `Platform::String^`.  Hodnota strukturám a třídám hodnota zkopírují hodnotou.  
  
 Hodnota struktury můžete provést s možnou hodnotou Null zabalení v IBox rozhraní.  
  
 Další informace najdete v tématu [hodnota třídy a struktury](../cppcx/value-classes-and-structs-c-cx.md).  
  
### <a name="partial-classes"></a>Částečné třídy  
 Funkce třídu umožňuje jednu třídu k definovat prostřednictvím více souborů. Použije se primárně k povolení nástrojů generování kódu, například editoru XAML pro úpravu jednoho souboru bez zásahu do souboru, který můžete upravit.  
  
 Další informace najdete v tématu [částečné třídy](../cppcx/partial-classes-c-cx.md)  
  
### <a name="properties"></a>Vlastnosti  
 Vlastnost je veřejná data člen jakéhokoli typu prostředí Windows Runtime a je implementovaný jako pár Metoda get/set. Kód klienta přístup k vlastnostem, jako kdyby nebylo veřejné pole. Získat vlastnosti, která vyžaduje žádné vlastní nebo sadu kódu se označuje jako *trivial vlastnost* a můžete deklarované bez explicitních get nebo metody set.  
  
 Další informace najdete v tématu [vlastnosti](../cppcx/properties-c-cx.md).  
  
### <a name="windows-runtime-collections-in-ccx"></a>Prostředí Windows Runtime kolekce v jazyce C + +/ CX  
 Prostředí Windows Runtime definuje sadu rozhraní pro typy kolekcí, které každý jazyk implementuje vlastní způsobem. C + +/ CX poskytuje implementace v [Platform::Collections::Vector třída](../cppcx/platform-collections-vector-class.md), [Platform::Collections::Map třída](../cppcx/platform-collections-map-class.md)a dalších typů související konkrétní kolekce, které jsou slučitelné s jejich Standardní šablona knihovny (STL) protějšky.  
  
 Další informace najdete v tématu [kolekce](../cppcx/collections-c-cx.md).  
  
### <a name="template-ref-classes"></a>Ref třídy šablon  
 Ref privátní a interní třídy je možné podle šablony a specializované.  
  
 Další informace najdete v tématu [třídy ref šablon](../cppcx/template-ref-classes-c-cx.md).  
  
### <a name="interfaces"></a>Rozhraní  
 Prostředí Windows Runtime rozhraní definuje sadu veřejné vlastnosti a metody, události, které ref třídě nebo struktuře ref musí implementovat, pokud se dědí z rozhraní.  
  
 Další informace najdete v tématu [rozhraní](../cppcx/interfaces-c-cx.md).  
  
### <a name="enums"></a>Výčty  
 Třídu enum v prostředí Windows Runtime podobá vymezená výčtu v jazyce C++. Základní typ je int32, pokud je použit atribut [příznaky] – v takovém případě je základní typ uint32.  
  
 Další informace najdete v tématu [výčty](../cppcx/enums-c-cx.md).  
  
### <a name="delegates"></a>Delegáty  
 Delegát v prostředí Windows Runtime je obdobou objekt std::function v jazyce C++. Je zvláštní druh ref třídu, která se použije k vyvolání funkce poskytované klienta, které mají kompatibilní podpisy.  Delegáti se běžně používají v prostředí Windows Runtime jako typ události.  
  
 Další informace najdete v tématu [delegáti](../cppcx/delegates-c-cx.md).  
  
### <a name="exceptions"></a>Výjimky  
 V jazyce C + +/ CX, můžete zachytit typy vlastní výjimek [std::exception](../standard-library/exception-class.md) typy, a [Platform::Exception](../cppcx/platform-exception-class.md) typy.  
  
 Další informace najdete v tématu [výjimky](../cppcx/exceptions-c-cx.md).  
  
### <a name="events"></a>Události  
 Událost je členem veřejné ve třídě ref nebo ref struct, jejichž typ je typ delegáta. Událost může být volána, pouze – to znamená, aktivováno – vlastnícím třídou. Kód klienta, ale může poskytovat vlastní funkce, které se označují jako obslužné rutiny událostí a jsou vyvolány při vlastnícím třída aktivuje událost.  
  
 Další informace najdete v tématu [události](../cppcx/events-c-cx.md).  
  
### <a name="casting"></a>Přetypování  
 C + +/ CX podporuje standardní operátory jazyka C++ přetypovat [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md), a [reinterpret_cast](../cpp/reinterpret-cast-operator.md)a také **safe_cast**operátor, který je specifická pro C + +/ CX.  
  
 Další informace najdete v tématu [přetypování](../cppcx/casting-c-cx.md).  
  
### <a name="boxing"></a>Zabalení  
 Pevně určené proměnné je hodnota typ, který je uzavřen do typu odkazu v situacích, kde jsou vyžadovány sémantiku odkaz.  
  
 Další informace najdete v tématu [zabalení](../cppcx/boxing-c-cx.md).  
  
### <a name="attributes"></a>Atributy  
 Atribut je hodnota metadat, která můžete použít u jakéhokoli typu prostředí Windows Runtime nebo člena typu a může být prověřovány za běhu. Definuje sadu běžné atributy v prostředí Windows Runtime `Windows::Foundation::Metadata` oboru názvů. Prostředí Windows Runtime v této verzi nepodporuje uživatelem definované atributy na veřejné rozhraní.  
  
## <a name="api-deprecation"></a>Zastaralá rozhraní API  
 Popisuje, jak označit veřejná rozhraní API jako zastaralé pomocí stejný atribut, který je používán systém typy prostředí Windows Runtime.  
  
 Další informace najdete v tématu [místo začne typy a členy](../cppcx/deprecating-types-and-members-c-cx.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)
