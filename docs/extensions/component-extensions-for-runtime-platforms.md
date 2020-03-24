---
title: Přípony komponent pro .NET a UPW
ms.date: 10/12/2018
ms.topic: overview
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: 6b3add1c0de8aa1f8ec66e8d220443c4a0efd704
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172462"
---
# <a name="component-extensions-for-net-and-uwp"></a>Přípony komponent pro .NET a UPW

C++ Standard umožňuje dodavatelům kompilátoru poskytnout nestandardní rozšíření pro jazyk. Společnost Microsoft poskytuje rozšíření, která vám pomůžou s připojením nativního C++ kódu ke kódu, který běží na .NET Framework nebo v Univerzální platforma Windows (UWP). Rozšíření .NET se nazývají C++/CLI a vytváří kód, který se spouští v prostředí pro spouštění spravovaném .NET, které se nazývá CLR (Common Language Runtime). Rozšíření UWP se nazývají C++/CX a vytváří nativní strojový kód.

> [!NOTE]
> U nových aplikací doporučujeme místo C++ C++/CX. používat/WinRT. C++/WinRT je nová standardní projekce jazyka C++ 17 pro prostředí Windows Runtime rozhraní API. Budeme dál podporovat C++/CX a WRL, ale důrazně doporučujeme, aby nové aplikace používaly C++/WinRT. Další informace najdete v tématu [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

### <a name="two-runtimes-one-set-of-extensions"></a>Dva moduly runtime, jedna sada rozšíření

C++/CLI rozšiřuje Standard ISO/ANSI C++ a definuje se ve standardu ECMA C++/CLI. Další informace najdete v tématu [programování .NET s C++/CLI (vizuál C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Rozšíření C++/CX jsou podmnožinou C++/CLI. I když je syntaxe rozšíření ve většině případů identická, generovaný kód závisí na tom, zda zadáte možnost kompilátoru `/ZW` pro prostředí UWP, nebo možnost `/clr` pro cílení na rozhraní .NET. Tyto přepínače jsou nastaveny automaticky při použití sady Visual Studio k vytvoření projektu.

## <a name="data-type-keywords"></a>Klíčová slova datového typu

Jazykové rozšíření obsahují *agregovaná klíčová slova*, která se skládají ze dvou tokenů oddělených prázdným znakem. Tokeny mohou mít jeden význam, pokud jsou používány samostatně, a další význam při použití společně. Například slovo "ref" je běžný identifikátor a slovo "Class" je klíčové slovo, které deklaruje nativní třídu. Pokud jsou však tato slova kombinována s **referenční třídou**Form, výsledné agregované klíčové slovo deklaruje entitu, která je známá jako *běhová třída*.

Rozšíření také obsahují *Kontextově závislá* klíčová slova. Klíčové slovo je považováno za kontextově závislé v závislosti na druhu příkazu, který obsahuje, a jeho umístění v tomto příkazu. Například token "Property" může být identifikátor nebo může deklarovat speciální druh člena veřejné třídy.

V následující tabulce jsou uvedena klíčová C++ slova v rozšíření jazyka.

|Klíčové slovo|Závislé na kontextu|Účel|Referenční informace|
|-------------|-----------------------|-------------|---------------|
|**ref class**<br /><br /> **struktura ref**|Ne|Deklaruje třídu.|[Třídy a struktury](classes-and-structs-cpp-component-extensions.md)|
|**Value – třída**<br /><br /> **struktura hodnoty**|Ne|Deklaruje hodnotovou třídu.|[Třídy a struktury](classes-and-structs-cpp-component-extensions.md)|
|**interface class**<br /><br /> **struktura rozhraní**|Ne|Deklaruje rozhraní.|[interface class](interface-class-cpp-component-extensions.md)|
|**enum class**<br /><br /> **struktura výčtu**|Ne|Deklaruje výčet.|[enum class](enum-class-cpp-component-extensions.md)|
|**property**|Ano|Deklaruje vlastnost.|[property](property-cpp-component-extensions.md)|
|**delegate**|Ano|Deklaruje delegáta.|[delegate (C++/CLI a C++/CX)](delegate-cpp-component-extensions.md)|
|**event**|Ano|Deklaruje událost.|[event](event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>override – specifikátory

Následující klíčová slova můžete použít k zařazování chování přepsání pro odvození. I když klíčové slovo **New** není rozšířením C++, je zde uvedeno, protože může být použito v dalším kontextu. Některé specifikátory jsou platné i pro nativní programování. Další informace naleznete v tématu [How to: Declare specifikátory přepisu v nativních kompilacích (C++/CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

|Klíčové slovo|Závislé na kontextu|Účel|Referenční informace|
|-------------|-----------------------|-------------|---------------|
|**abstract**|Ano|Označuje, že funkce nebo třídy jsou abstraktní.|[abstract](abstract-cpp-component-extensions.md)|
|**new**|Ne|Označuje, že funkce není popsána ve verzi základní třídy.|[new (nový slot v tabulce vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|Ano|Označuje, že metoda musí být přepsání verze základní třídy.|[override](override-cpp-component-extensions.md)|
|**sealed**|Ano|Zabraňuje použití tříd jako základních tříd.|[sealed](sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>Klíčová slova pro obecné typy

Následující klíčová slova byla přidána pro podporu generických typů. Další informace najdete v tématu [Obecné typy](generics-cpp-component-extensions.md).

|Klíčové slovo|Závislé na kontextu|Účel|
|-------------|-----------------------|-------------|
|**Obecněji**|Ne|Deklaruje obecný typ.|
|**,**|Ano|Určuje omezení, která se aplikují na parametr obecného typu.|

## <a name="miscellaneous-keywords"></a>Různá klíčová slova

Do C++ rozšíření byla přidána následující klíčová slova.

|Klíčové slovo|Závislé na kontextu|Účel|Referenční informace|
|-------------|-----------------------|-------------|---------------|
|**finally**|Ano|Označuje chování výchozí zpracování výjimek.|[Zpracování výjimek](exception-handling-cpp-component-extensions.md)|
|**for each, in**|Ne|Vytvoří výčet prvků kolekce.|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|Ne|Přiděluje typy pro haldu uvolňování paměti. Místo **New** a **Delete**použijte.|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**ref new**|Ano|Přidělí prostředí Windows Runtime typ. Místo **New** a **Delete**použijte.|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|Ano|Označuje, že člen může být inicializován pouze v deklaraci nebo ve statickém konstruktoru.|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**literal**|Ano|Vytvoří proměnnou literálu.|[literal](literal-cpp-component-extensions.md)|
|**nullptr**|Ne|Označuje, že popisovač nebo ukazatel neukazuje na objekt.|[nullptr](nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>Konstrukce šablon

Následující jazykové konstrukce jsou implementovány jako šablony namísto klíčová slova. Zadáte-li možnost kompilátoru `/ZW`, jsou definovány v oboru názvů `lang`. Zadáte-li možnost kompilátoru `/clr`, jsou definovány v oboru názvů `cli`.

|Klíčové slovo|Účel|Referenční informace|
|-------------|-------------|---------------|
|**skupin**|Deklaruje pole.|[Pole](arrays-cpp-component-extensions.md)|
|**interior_ptr**|(Jenom CLR) Odkazuje na data v typu odkazu.|[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)|
|**pin_ptr**|(Jenom CLR) Odkazuje na referenční typy CLR pro dočasné potlačení systému uvolňování paměti.|[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)|
|**safe_cast**|Určuje a spustí optimální metodu přetypování pro typ modulu runtime.|[safe_cast](safe-cast-cpp-component-extensions.md)|
|**typeid**|(Jenom CLR) Načte objekt <xref:System.Type?displayProperty=fullName>, který popisuje daný typ nebo objekt.|[typeid](typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>Deklarátory

Následující typ deklarátory instruuje modul runtime, aby automaticky spravoval dobu života a odstraňování přidělených objektů.

|Operátor|Účel|Referenční informace|
|--------------|-------------|---------------|
|`^`|Deklaruje popisovač objektu; To znamená, že ukazatel na objekt prostředí Windows Runtime nebo CLR, který je automaticky odstraněn, když již není použitelný.|[Operátor popisovače objektu (^)](handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|Deklaruje sledovací odkaz; To znamená odkaz na objekt prostředí Windows Runtime nebo CLR, který je automaticky odstraněn, když již není použitelný.|[Operátor sledovacího odkazu](tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>Další konstrukce a Příbuzná témata

Tato část obsahuje seznam dalších programovacích konstrukcí a témata, která se týkají CLR.

|Téma|Popis|
|-----------|-----------------|
|[__identifier (C++/CLI)](identifier-cpp-cli.md)|(Prostředí Windows Runtime a CLR) Povoluje použití klíčových slov jako identifikátorů.|
|[Seznamy argumentů s proměnnou délkou (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Prostředí Windows Runtime a CLR) Umožňuje, aby funkce převzala proměnlivý počet argumentů.|
|[.NET Framework – ekvivalenty nativních typů C++ (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Obsahuje seznam typů CLR, které se používají místo C++ celočíselných typů.|
|[appdomain](../cpp/appdomain.md) **__declspec** modifikátor domény aplikace|Modifikátor **__declspec** , který stanoví, že existují statické a globální proměnné pro doménu AppDomain.|
|[Přetypování ve stylu jazyka C s možnostíC++/CLR (/CLI)](c-style-casts-with-clr-cpp-cli.md)|Popisuje způsob interpretace přetypování ve stylu jazyka C.|
|[__clrcall](../cpp/clrcall.md) konvence volání|Označuje konvenci volání kompatibilní s modulem CLR.|
|`__cplusplus_cli`|[Předdefinovaná makra](../preprocessor/predefined-macros.md)|
|[Vlastní atributy](user-defined-attributes-cpp-component-extensions.md)|Popisuje, jak definovat vlastní atributy CLR.|
|[Zpracování výjimek](exception-handling-cpp-component-extensions.md)|Poskytuje přehled o zpracování výjimek.|
|[Explicitní přepsání](explicit-overrides-cpp-component-extensions.md)|Ukazuje, jak členské funkce mohou přepsat libovolné členy.|
|[Přátelská sestavení (C++)](../dotnet/friend-assemblies-cpp.md)|Popisuje, jak může klientské sestavení přistupovat ke všem typům v součásti sestavení.|
|[Zabalení](boxing-cpp-component-extensions.md)|Ukazuje podmínky, které jsou typy hodnot v krabici.|
|[Podpora kompilátoru pro typové vlastnosti](compiler-support-for-type-traits-cpp-component-extensions.md)|Popisuje, jak detekovat charakteristiky typů v době kompilace.|
|[spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy pragma|Ukazuje, jak mohou spravované a nespravované funkce existovat společně ve stejném modulu.|
|Modifikátor [procesu](../cpp/process.md) **__declspec**|**__declspec** modifikátor, který stanoví, že statické a globální proměnné existují pro proces.|
|[Reflexe (C++/CLI)](../dotnet/reflection-cpp-cli.md)|Ukazuje verzi CLR informací o typu modulu runtime.|
|[Řetězec](string-cpp-component-extensions.md)|Popisuje převod kompilátoru pro řetězcové literály na <xref:System.String>.|
|[Předávání typů (C++/CLI)](type-forwarding-cpp-cli.md)|Povoluje přesun typu v lodním sestavení do jiného sestavení tak, aby kód klienta nebylo nutné znovu kompilovat.|
|[Uživatelsky definované atributy](user-defined-attributes-cpp-component-extensions.md)|Ukazuje uživatelsky definované atributy.|
|[#using direktiva](../preprocessor/hash-using-directive-cpp.md)|Importuje externí sestavení.|
|[Dokumentace XML](../build/reference/xml-documentation-visual-cpp.md)|Vysvětluje dokumentaci kódu založenou na jazyce XML pomocí [/doc (zpracování dokumentačních komentářů) (C++C/)](../build/reference/doc-process-documentation-comments-c-cpp.md)|

## <a name="see-also"></a>Viz také

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)
