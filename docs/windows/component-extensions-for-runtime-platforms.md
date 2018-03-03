---
title: "Rozšíření komponent pro platformy běhového prostředí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- Visual C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e32057e17614da98c78d877fe95180dd02500909
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="component-extensions-for-runtime-platforms"></a>Přípony komponent pro platformy běhového prostředí
Visual C++ poskytuje jazyková rozšíření pomohou program pro platformy běhového prostředí. Pomocí C + +/ CX, můžete naprogramovat aplikace pro univerzální platformu Windows a součástí, které kompilace nativního kódu. I když aplikace pro univerzální platformu Windows můžete vytvořit pomocí programování přímo na rozhraní Windows Runtime COM pomocí C + +/ CX, můžete pracovat s konstruktory výjimky a další moderní verze jazyka C++ programování idioms. Chcete-li povolit C++ programování v spravovaného spouštění prostředí na platformě .NET, můžete použít C + +/ CLI.  
  
 **Dva moduly runtime, jednu sadu rozšíření**  
  
 C + +/ CX je podmnožinou C + +/ CLI. Pro rozšíření, které jsou společné pro C + +/ CX a C + +/ CLI, sémantika závisí na tom, zda cílíte na modul CLR (CLR) nebo prostředí Windows Runtime. Kompilace aplikaci, kterou chcete spustit v prostředí Windows Runtime, zadejte **/ZW** – možnost kompilátoru. Kompilace jeho spuštění v modulu CLR, zadejte **/CLR** – možnost kompilátoru. Tyto přepínače jsou automaticky nastavit pomocí sady Visual Studio k vytvoření projektu.  
  
 Další informace o tom, jak vytvářet aplikace pro univerzální platformu Windows v jazyce C++ najdete v tématu [plán pro prostředí Windows Runtime aplikací pomocí C++](http://msdn.microsoft.com/library/windows/apps/hh700360.aspx).  
  
 C + +/ CLI rozšiřuje standard ISO/ANSI C++ a je definována v části s Ecma C + +/ CLI standardní. Další informace najdete v tématu [.NET programování v jazyce C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
## <a name="data-type-keywords"></a>Klíčová slova datový typ  
 Jazyková rozšíření zahrnují *agregovat klíčová slova*, které jsou klíčová slova, které se skládají ze dvou tokeny oddělených mezer. Tokeny může mít jeden význam při použití samostatně a jiný význam při použití společně. Například běžný identifikátor je slovo "ref" a slovo "třída" je klíčové slovo, který deklaruje nativních tříd. Ale když se tato slova zkombinují do formuláře `ref class`, výsledná agregační – klíčové slovo deklaruje entita, která se označuje jako *runtime třídy*.  
  
 Rozšíření také zahrnovat *kontextová* klíčová slova. Klíčové slovo je zpracovaná jako kontextová v závislosti na druhu příkaz, který obsahuje a jeho umístění v tomto příkazu. Například token "vlastnost" může být identifikátor nebo ho můžou deklarovat zvláštní druh člen veřejné třídy.  
  
 Následující tabulka uvádí klíčová slova v rozšíření jazyka C++.  
  
|– Klíčové slovo|Závislé na kontextu|Účel|Odkaz|  
|-------------|-----------------------|-------------|---------------|  
|`ref class`<br /><br /> `ref struct`|Ne|Deklaruje třídu.|[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`value class`<br /><br /> `value struct`|Ne|Deklaruje – hodnotová třída.|[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`interface class`<br /><br /> `interface struct`|Ne|Deklaruje rozhraní.|[Třída rozhraní](../windows/interface-class-cpp-component-extensions.md)|  
|`enum class`<br /><br /> `enum struct`|Ne|Deklaruje výčet.|[enum – třída](../windows/enum-class-cpp-component-extensions.md)|  
|`property`|Ano|Deklaruje vlastnost.|[property](../windows/property-cpp-component-extensions.md)|  
|`delegate`|Ano|Deklaruje delegáta.|[delegate (rozšíření komponent C++)](../windows/delegate-cpp-component-extensions.md)|  
|`event`|Ano|Deklaruje událost.|[event](../windows/event-cpp-component-extensions.md)|  
  
## <a name="override-specifiers"></a>override – specifikátory  
 K určení chování přepsání pro odvození můžete použít následující klíčová slova. I když `new` – klíčové slovo není rozšíření c++, je uvedena jako zde protože je možné použít v kontextu Další. Některé specifikátory platí také pro nativní programování. Další informace najdete v tématu [postupy: deklarace specifikátorů Override v nativní kompilaci (C + +/ CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
|– Klíčové slovo|Závislé na kontextu|Účel|Odkaz|  
|-------------|-----------------------|-------------|---------------|  
|`abstract`|Ano|Označuje, že funkce nebo třídy jsou abstraktní.|[abstract](../windows/abstract-cpp-component-extensions.md)|  
|`new`|Ne|Označuje, že je funkce není přepsání verze základní třídy.|[New (nový slot v tabulce vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|  
|`override`|Ano|Označuje, že metoda musí být přepsání verze základní třídy.|[override](../windows/override-cpp-component-extensions.md)|  
|`sealed`|Ano|Třídy brání použití jako základní třídy.|[sealed](../windows/sealed-cpp-component-extensions.md)|  
  
## <a name="keywords-for-generics"></a>Klíčová slova pro obecné typy  
 Pro podporu obecných typů byly přidány následující klíčová slova. Další informace najdete v tématu [obecné typy](../windows/generics-cpp-component-extensions.md).  
  
|– Klíčové slovo|Závislé na kontextu|Účel|  
|-------------|-----------------------|-------------|  
|`generic`|Ne|Deklaruje obecného typu.|  
|`where`|Ano|Určuje omezení, která se použijí pro parametr obecného typu.|  
  
## <a name="miscellaneous-keywords"></a>Různé klíčová slova  
 Rozšíření C++ přidané následující klíčová slova.  
  
|– Klíčové slovo|Závislé na kontextu|Účel|Odkaz|  
|-------------|-----------------------|-------------|---------------|  
|`finally`|Ano|Určuje výchozí chování handlings výjimka.|[Zpracování výjimek](../windows/exception-handling-cpp-component-extensions.md)|  
|`for each, in`|Ne|Vytvoří výčet prvků kolekce.|[for each, in](../dotnet/for-each-in.md)|  
|`gcnew`|Ne|Přiděluje typy v haldě uvolňování paměti. Použít místo `new` a `delete`.|[nové, gcnew REF](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`ref new`|Ano|Přiděluje typu prostředí Windows Runtime. Použít místo `new` a `delete`.|[nové, gcnew REF](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`initonly`|Ano|Označuje členem lze inicializovat pouze v prohlášení nebo ve statického konstruktoru.|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|  
|`literal`|Ano|Vytvoří literálu proměnnou.|[literál](../windows/literal-cpp-component-extensions.md)|  
|`nullptr`|Ne|Označuje, že popisovač nebo ukazatel neodkazuje na objekt.|[nullptr](../windows/nullptr-cpp-component-extensions.md)|  
  
## <a name="template-constructs"></a>Konstrukce šablony  
 Následující jazykové konstrukty jsou implementované jako šablona, místo jako klíčová slova. Pokud zadáte **/ZW** – možnost kompilátoru, jsou definovány v `lang` oboru názvů. Pokud zadáte **/CLR** – možnost kompilátoru, jsou definovány v `cli` oboru názvů.  
  
|– Klíčové slovo|Účel|Odkaz|  
|-------------|-------------|---------------|  
|`array`|Deklaruje pole.|[Pole](../windows/arrays-cpp-component-extensions.md)|  
|`interior_ptr`|(Jenom CLR) Body k datům v odkazového typu.|[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)|  
|`pin_ptr`|(Jenom CLR) Odkazuje na odkazové typy CLR dočasně potlačit systém kolekce paměti.|[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)|  
|`safe_cast`|Určuje a provede metodu optimální přetypování pro typ modulu runtime.|[safe_cast](../windows/safe-cast-cpp-component-extensions.md)|  
|`typeid`|(Jenom CLR) Načte <xref:System.Type?displayProperty=fullName> objekt, který popisuje daný typ nebo objekt.|[typeid](../windows/typeid-cpp-component-extensions.md)|  
  
## <a name="declarators"></a>Deklarátory  
 Následující deklarátory typ dá pokyn modulu runtime automaticky Správa životního cyklu a odstranění přidělené objektů.  
  
|Operátor|Účel|Odkaz|  
|--------------|-------------|---------------|  
|`^`|Deklaruje popisovač pro objekt; To znamená, ukazatel na prostředí Windows Runtime nebo CLR objekt, který je automaticky odstraněn, když už není použitelná.|[Operátor popisovače objektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|  
|`%`|Deklaruje sledovací odkaz; To znamená, odkaz na prostředí Windows Runtime nebo CLR objekt, který je automaticky odstraněn, když už není použitelná.|[Operátor sledovacího odkazu](../windows/tracking-reference-operator-cpp-component-extensions.md)|  
  
## <a name="additional-constructs-and-related-topics"></a>Další konstrukce a související témata  
 Tato část obsahuje další programovací konstrukce a témata, která se týkají modulu CLR.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[__identifier (C++/CLI)](../windows/identifier-cpp-cli.md)|(Prostředí Windows Runtime a CLR) Umožňuje použití klíčová slova jako identifikátory.|  
|[Seznamy argumentů s proměnnou délkou (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Prostředí Windows Runtime a CLR) Povolí funkci, kterou chcete provést proměnný počet argumentů.|  
|[.NET Framework – ekvivalenty nativních typů C++ (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Seznam typů CLR, které se používají místo integrální typy C++.|  
|[doména AppDomain](../cpp/appdomain.md) `__declspec` – modifikátor|`__declspec`Modifikátor, který vyžaduje, aby statické a globální proměnné existovat jednotlivé domény aplikace.|  
|[Přetypování ve stylu jazyka pomocí možnosti/CLR (C + +/ CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)|Popisuje, jak se interpretují přetypování ve stylu jazyka.|  
|[__clrcall](../cpp/clrcall.md) konvence volání|Označuje kompatibilní se standardem CLR konvence volání.|  
|`__cplusplus_cli`|[Předdefinovaná makra](../preprocessor/predefined-macros.md)|  
|[Vlastní atributy](../windows/custom-attributes-cpp.md)|Popisuje, jak definovat vlastní atributy CLR.|  
|[Zpracování výjimek](../windows/exception-handling-cpp-component-extensions.md)|Poskytuje přehled o zpracování výjimek.|  
|[Explicitní přepsání](../windows/explicit-overrides-cpp-component-extensions.md)|Ukazuje, jak členské funkce můžete přepsat libovolný členy.|  
|[Přátelská sestavení (C++)](../dotnet/friend-assemblies-cpp.md)|Popisuje, jak klienta sestavení přístupné všechny typy v komponentu sestavení.|  
|[Zabalení](../windows/boxing-cpp-component-extensions.md)|Demonstruje podmínky v hodnot, které jsou do pole typů.|  
|[Podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|Popisuje, jak zjistit vlastnosti typů v době kompilace.|  
|[spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivách pragma|Ukazuje, jak spravovaných a nespravovaných funkcí mohou společně existovat ve stejném modulu.|  
|[proces](../cpp/process.md) `__declspec` – modifikátor|`__declspec`Modifikátor, který vyžaduje, aby statické a globální proměnné existovat podle procesu.|  
|[Reflexe (C++/CLI)](../dotnet/reflection-cpp-cli.md)|Demonstruje verzi informace běhového typu CLR.|  
|[Řetězec](../windows/string-cpp-component-extensions.md)|Popisuje převod kompilátoru textových literálů k <xref:System.String>.|  
|[Předávání typů (C++/CLI)](../windows/type-forwarding-cpp-cli.md)|Přesun k typu v sestavení přesouvání do jiného sestavení umožňuje, aby kód klienta není nutné zopakovat.|  
|[Uživatelsky definované atributy](../windows/user-defined-attributes-cpp-component-extensions.md)|Demonstruje uživatelsky definované atributy.|  
|[#using – direktiva](../preprocessor/hash-using-directive-cpp.md)|Importuje externí sestavení.|  
|[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)|Vysvětluje kódu XML na dokumentaci pomocí  [ /DOC (zpracování dokumentačních komentářů) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
  
## <a name="see-also"></a>Viz také  
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)