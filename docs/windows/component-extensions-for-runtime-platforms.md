---
title: Přípony komponent pro platformy běhového prostředí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- Visual C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a9fa20fc180d9b77f5d909ea06d12d69c1ef89d1
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652682"
---
# <a name="component-extensions-for-runtime-platforms"></a>Přípony komponent pro platformy běhového prostředí
Visual C++ poskytuje rozšíření jazyka pomoci programovat proti platformy běhového prostředí. S použitím C + +/ CX, při programování aplikací pro univerzální platformu Windows a komponenty, které se kompilují do nativního kódu. I když můžete vytvořit aplikace pro univerzální platformu Windows pomocí programování přímo proti rozhraní Windows Runtime COM s použitím C + +/ CX, můžete pracovat s konstruktory, výjimek a jiné moderní programovací idiomy C++. Pokud chcete povolit programování C++ ve spravovaném spouštěcím prostředí na platformě .NET, můžete použít C + +/ CLI.  
  
### <a name="two-runtimes-one-set-of-extensions"></a>Dva moduly runtime, jednu sadu rozšíření  
  
 C + +/ CX je podmnožinou jazyka C + +/ CLI. Pro rozšíření, které jsou společné pro C + +/ CX a C + +/ CLI, sémantika závisí na tom, zda cílíte na modul CLR (CLR) nebo prostředí Windows Runtime. Chcete-li zkompilovat aplikaci pro spuštění v modulu Windows Runtime, zadejte `/ZW` – možnost kompilátoru. Chcete-li zkompilovat jeho spuštění na modulu CLR, zadejte `/clr` – možnost kompilátoru. Tyto přepínače jsou nastaveny automaticky při vytvoření projektu pomocí sady Visual Studio.  
  
 Další informace o vytváření aplikací pro univerzální platformu Windows v jazyce C++ naleznete v tématu [plán pro prostředí Windows Runtime aplikací pomocí C++](http://msdn.microsoft.com/library/windows/apps/hh700360.aspx).  
  
 C + +/ CLI rozšiřuje standard ISO/ANSI C++ a je definován v části s Ecma C + +/ CLI Standard. Další informace najdete v tématu [.NET programování v jazyce C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
## <a name="data-type-keywords"></a>Klíčová slova datový typ  
 Jazyková rozšíření zahrnují *agregovat klíčová slova*, které jsou klíčová slova, které se skládají ze dvou tokeny oddělené symbolem mezery. Tokeny může mít jeden význam při použití samostatně a jiný význam při použití společně. Například slovo "ref" je běžný identifikátor a slovo "třída" je klíčové slovo, který deklaruje nativních tříd. Ale když se tato slova kombinovány do **třídy ref class**, výsledný agregační – klíčové slovo deklaruje entita, která se označuje jako *runtime třídy*.  
  
 Rozšíření také zahrnovat *kontextové* klíčová slova. Klíčové slovo je zpracováván jako kontextové v závislosti na typu příkazu, který obsahuje a jeho umístění v, který tento příkaz. Například token "vlastnosti" může být identifikátor nebo ho můžete deklarovat zvláštní druh člena veřejné třídy.  
  
 Následující tabulka obsahuje seznam klíčových slov v rozšíření jazyka C++.  
  
|Klíčové slovo|Závislá na kontextu|Účel|Odkaz|  
|-------------|-----------------------|-------------|---------------|  
|**třídy ref class.**<br /><br /> **REF – struktura**|Ne|Deklaruje třídu.|[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)|  
|**hodnotová třída**<br /><br /> **Hodnota – struktura**|Ne|Deklaruje hodnotové třídě.|[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)|  
|**Třída rozhraní**<br /><br /> **Struktura rozhraní**|Ne|Deklaruje rozhraní.|[Třída rozhraní](../windows/interface-class-cpp-component-extensions.md)|  
|**Třída výčtu**<br /><br /> **Struktura výčet**|Ne|Deklaruje výčet.|[Třída výčtu](../windows/enum-class-cpp-component-extensions.md)|  
|**property**|Ano|Deklaruje vlastnost.|[property](../windows/property-cpp-component-extensions.md)|  
|**delegate**|Ano|Deklaruje delegáta.|[delegate (rozšíření komponent C++)](../windows/delegate-cpp-component-extensions.md)|  
|**event**|Ano|Deklaruje událost.|[event](../windows/event-cpp-component-extensions.md)|  
  
## <a name="override-specifiers"></a>override – specifikátory  
 Následující klíčová slova můžete použít k určení chování přepsat pro odvození. I když **nové** – klíčové slovo není rozšířením jazyka C++, je vzhledem k tomu je možné v další kontext zde uvedena. Několik specifikátorů platí také pro nativní programování. Další informace najdete v tématu [jak: deklarovat specifikátorů Override v nativní kompilaci (C + +/ CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
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
|**InitOnly.**|Ano|Označuje, že člen se dá inicializovat jenom v deklaraci nebo statický konstruktor.|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|  
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
|[doména AppDomain](../cpp/appdomain.md) **__declspec** modifikátor|**__declspec** modifikátor, který určuje, že existují statické a globální proměnné na doménu aplikace.|  
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
|[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)|Vysvětluje dokumentace kódu XML pomocí  [ /DOC (zpracování dokumentačních komentářů) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
  
## <a name="see-also"></a>Viz také  
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)