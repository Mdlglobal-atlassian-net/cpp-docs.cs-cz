---
title: Přípony komponent pro .NET a UPW
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: e9586244c9e2293ba6b484efb158fc3a2529c0ea
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "57814485"
---
# <a name="component-extensions-for-net-and-uwp"></a>Přípony komponent pro .NET a UPW

Standard jazyka C++ umožňuje dodavatelům kompilátoru poskytují nestandardní rozšíření pro jazyk. Microsoft poskytuje rozšíření vám pomůže s připojením nativní kód C++ pro kód, který běží na rozhraní .NET Framework nebo univerzální platformu Windows (UPW). Rozšíření .NET se nazývají C + +/ CLI a vytvoří kód, který se spustí v rozhraní .NET spravované prostředí pro spouštění, která je volána Common Language Runtime (CLR). Rozšíření UPW se nazývají C + +/ CX a vytvořit nativního strojového kódu.

> [!NOTE]
> Pro nové aplikace, doporučujeme použít C + +/ WinRT spíše než C + +/ CX. C + +/ WinRT je nový, standard C ++ 17 jazyk projekci pro rozhraní API Windows Runtime. Budeme dál podporovat C + +/ CX a WRL, ale důrazně doporučujeme, aby nové aplikace pomocí C + +/ WinRT. Další informace najdete v tématu [C + +/ WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).

### <a name="two-runtimes-one-set-of-extensions"></a>Dva moduly runtime, jednu sadu rozšíření

C + +/ CLI rozšiřuje standard ISO/ANSI C++ a je definován v části s Ecma C + +/ CLI Standard. Další informace najdete v tématu [.NET programování v jazyce C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

C + +/ CX rozšíření jsou podmnožinou C + +/ CLI. I když rozšíření syntaxe je stejný jako ve většině případů, kód, který je generován závisí na, jestli je zadat `/ZW` – možnost kompilátoru do cíle UPW, nebo `/clr` možnost cílového rozhraní .NET. Tyto přepínače jsou nastaveny automaticky při vytvoření projektu pomocí sady Visual Studio.

## <a name="data-type-keywords"></a>Klíčová slova datový typ

Jazyková rozšíření zahrnují *agregovat klíčová slova*, které jsou tvořeny dva tokeny oddělené symbolem mezery. Tokeny může mít jeden význam při použití samostatně a jiný význam při použití společně. Například slovo "ref" je běžný identifikátor a slovo "třída" je klíčové slovo, který deklaruje nativních tříd. Ale když se tato slova kombinovány do **třídy ref class**, výsledný agregační – klíčové slovo deklaruje entita, která se označuje jako *runtime třídy*.

Rozšíření také zahrnovat *kontextové* klíčová slova. Klíčové slovo je zpracováván jako kontextové v závislosti na typu příkazu, který obsahuje a jeho umístění v, který tento příkaz. Například token "vlastnosti" může být identifikátor nebo ho můžete deklarovat zvláštní druh člena veřejné třídy.

Následující tabulka obsahuje seznam klíčových slov v rozšíření jazyka C++.

|Klíčové slovo|Závislá na kontextu|Účel|Odkaz|
|-------------|-----------------------|-------------|---------------|
|**třídy ref class.**<br /><br /> **REF – struktura**|Ne|Deklaruje třídu.|[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)|
|**hodnotová třída**<br /><br /> **Hodnota – struktura**|Ne|Deklaruje hodnotové třídě.|[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)|
|**Třída rozhraní**<br /><br /> **Struktura rozhraní**|Ne|Deklaruje rozhraní.|[Třída rozhraní](../windows/interface-class-cpp-component-extensions.md)|
|**Třída výčtu**<br /><br /> **Struktura výčet**|Ne|Deklaruje výčet.|[Třída výčtu](../windows/enum-class-cpp-component-extensions.md)|
|**property**|Ano|Deklaruje vlastnost.|[property](../windows/property-cpp-component-extensions.md)|
|**delegate**|Ano|Deklaruje delegáta.|[delegate (C++/CLI a C++/CX)](../windows/delegate-cpp-component-extensions.md)|
|**event**|Ano|Deklaruje událost.|[event](../windows/event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>override – specifikátory

Následující klíčová slova můžete použít k určení chování přepsat pro odvození. I když **nové** – klíčové slovo není rozšířením jazyka C++, je vzhledem k tomu je možné v další kontext zde uvedena. Několik specifikátorů platí také pro nativní programování. Další informace najdete v tématu [jak: Deklarace specifikátorů Override v nativních kompilacích (C + +/ CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

|Klíčové slovo|Závislá na kontextu|Účel|Odkaz|
|-------------|-----------------------|-------------|---------------|
|**abstract**|Ano|Určuje, že jsou abstraktní funkcí nebo tříd.|[abstract](../windows/abstract-cpp-component-extensions.md)|
|**new**|Ne|Označuje, že funkce není přepsání verze základní třídy.|[New (nový slot v tabulce vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|Ano|Označuje, že metoda musí být přepsání verze základní třídy.|[override](../windows/override-cpp-component-extensions.md)|
|**sealed**|Ano|Třídy brání použití jako základní třídy.|[sealed](../windows/sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>Klíčová slova pro obecné typy

Byly přidány následující klíčová slova pro podporu obecných typů. Další informace najdete v tématu [obecných typů](../windows/generics-cpp-component-extensions.md).

|Klíčové slovo|Závislá na kontextu|Účel|
|-------------|-----------------------|-------------|
|**Obecné**|Ne|Deklaruje obecného typu.|
|**kde**|Ano|Určuje omezení, která se použijí na parametr obecného typu.|

## <a name="miscellaneous-keywords"></a>Ostatní klíčová slova

Následující klíčová slova jsou přidané do rozšíření C++.

|Klíčové slovo|Závislá na kontextu|Účel|Odkaz|
|-------------|-----------------------|-------------|---------------|
|**finally**|Ano|Určuje výchozí chování handlings výjimky.|[Zpracování výjimek](../windows/exception-handling-cpp-component-extensions.md)|
|**for each, in**|Ne|Vytvoří výčet prvků kolekce.|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|Ne|Přidělí typy v haldě uvolňování paměti. Použít místo **nové** a **odstranit**.|[REF new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**Nový odkaz**|Ano|Přidělí typ Windows Runtime. Použít místo **nové** a **odstranit**.|[REF new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|Ano|Označuje, že člen se dá inicializovat jenom v deklaraci nebo statický konstruktor.|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**literál**|Ano|Vytvoří proměnnou literálu.|[literál](../windows/literal-cpp-component-extensions.md)|
|**nullptr**|Ne|Označuje, že popisovač nebo ukazatel neukazuje na objekt.|[nullptr](../windows/nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>Šablona konstrukce

Tyto jazykové konstrukce jsou implementovány jako šablony, nikoli jako klíčová slova. Pokud zadáte `/ZW` – možnost kompilátoru, jsou definovány v `lang` oboru názvů. Pokud zadáte `/clr` – možnost kompilátoru, jsou definovány v `cli` oboru názvů.

|Klíčové slovo|Účel|Odkaz|
|-------------|-------------|---------------|
|**Pole**|Deklaruje pole.|[Pole](../windows/arrays-cpp-component-extensions.md)|
|**interior_ptr**|(Pouze CLR) Body k datům v typu odkazu.|[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)|
|**pin_ptr**|(Pouze CLR) Odkazuje na odkazové typy CLR dočasně potlačit systém kolekce paměti.|[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)|
|**safe_cast**|Určuje a provede metodu optimální přetypování typu modulu runtime.|[safe_cast](../windows/safe-cast-cpp-component-extensions.md)|
|**identifikátor TypeId.**|(Pouze CLR) Načte <xref:System.Type?displayProperty=fullName> objekt, který popisuje daného typu nebo objekt.|[identifikátor TypeId.](../windows/typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>Deklarátory

Následující typ deklarátory dáte pokyn, aby modul runtime k automatické správě životního cyklu a odstranění přidělených objektů.

|Operátor|Účel|Odkaz|
|--------------|-------------|---------------|
|`^`|Deklaruje popisovač pro objekt; To znamená, ukazatel na objekt prostředí Windows Runtime nebo CLR, který se automaticky odstraní, když už není použitelný.|[Operátor popisovače objektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|Deklaruje odkazem sledování.; To znamená, že odkaz na objekt prostředí Windows Runtime nebo CLR, který se automaticky odstraní, když už není použitelný.|[Operátor sledovacího odkazu](../windows/tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>Další konstrukce a související témata

Tato část obsahuje další programovací konstrukce a témata, která se týkají modulu CLR.

|Téma|Popis|
|-----------|-----------------|
|[__identifier (C++/CLI)](../windows/identifier-cpp-cli.md)|(Windows Runtime a CLR) Umožňuje použít klíčová slova jako identifikátory.|
|[Seznamy argumentů s proměnnou délkou (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Windows Runtime a CLR) Povolí funkci provést proměnný počet argumentů.|
|[.NET Framework – ekvivalenty nativních typů C++ (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Seznam typů CLR, které se používají místo celočíselné typy C++.|
|[appdomain](../cpp/appdomain.md) **__declspec** modifier|**__declspec** modifikátor, který určuje, že existují statické a globální proměnné na doménu aplikace.|
|[Přetypování C-Style s parametrem/CLR (C + +/ CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)|Popisuje, jak se interpretují přetypování C-style.|
|[výraz __clrcall](../cpp/clrcall.md) konvence volání|Určuje konvence volání CLR nedodržující předpisy.|
|`__cplusplus_cli`|[Předdefinovaná makra](../preprocessor/predefined-macros.md)|
|[Vlastní atributy](../windows/custom-attributes-cpp.md)|Popisuje, jak definovat vlastní atributy CLR.|
|[Zpracování výjimek](../windows/exception-handling-cpp-component-extensions.md)|Poskytuje přehled o zpracování výjimek.|
|[Explicitní přepsání](../windows/explicit-overrides-cpp-component-extensions.md)|Ukazuje, jak můžete členské funkce přepsat libovolné členy.|
|[Přátelská sestavení (C++)](../dotnet/friend-assemblies-cpp.md)|Tento článek popisuje, jak sestavení klienta můžete získat přístup k všechny typy v jako součást sestavení.|
|[Zabalení](../windows/boxing-cpp-component-extensions.md)|Ukazuje podmínky v hodnot, které jsou v poli typy.|
|[Podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|Popisuje, jak detekovat vlastnosti typů v době kompilace.|
|[spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy pragma|Ukazuje, jak spravované a nespravované funkce mohou současně existovat ve stejném modulu.|
|[proces](../cpp/process.md) **__declspec** modifikátor|**__declspec** modifikátor, který zmocňuje, statické a globální proměnné existují jeden proces.|
|[Reflexe (C++/CLI)](../dotnet/reflection-cpp-cli.md)|Ukazuje CLR verze informací o typu za běhu.|
|[řetězec](../windows/string-cpp-component-extensions.md)|Tento článek popisuje kompilátoru převod z řetězcových literálů na <xref:System.String>.|
|[Předávání typů (C++/CLI)](../windows/type-forwarding-cpp-cli.md)|Přesun typu do přesouvání sestavení na jiné sestavení umožňuje, aby se klientský kód nebude muset být překompilovány.|
|[Uživatelsky definované atributy](../windows/user-defined-attributes-cpp-component-extensions.md)|Ukazuje, uživatelsky definované atributy.|
|[#using – direktiva](../preprocessor/hash-using-directive-cpp.md)|Importuje externí sestavení.|
|[Dokumentace XML](../build/reference/xml-documentation-visual-cpp.md)|Vysvětluje dokumentace kódu XML pomocí  [ /DOC (zpracování dokumentačních komentářů) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md)|

## <a name="see-also"></a>Viz také

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)