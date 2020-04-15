---
title: '#import – direktiva (C++)'
ms.date: 08/29/2019
f1_keywords:
- '#import'
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
ms.openlocfilehash: 9cdfef091b659151f427c381e386f0e83396e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332057"
---
# <a name="import-directive-c"></a>#import direktiva (C++)

**Specifické pro C++**

Slouží k začlenění informací z knihovny typů. Obsah knihovny typů je převeden na třídy Jazyka C++, většinou popisující rozhraní MODELU COM.

## <a name="syntax"></a>Syntaxe

> **#import** " název \[*souboru*" *atributy*]\
> **#import** \<> \[*atributy* *názvu souboru*]

### <a name="parameters"></a>Parametry

*Název_souboru*\
Určuje knihovnu typů, kterou chcete importovat. *Název souboru* může být jeden z následujících druhů:

- Název souboru, který obsahuje knihovnu typů, například soubor .olb, TLB nebo DLL. Klíčové slovo `file:`, může předcházet každému názvu souboru.

- Progid ovládacího prvku v knihovně typů. Klíčové slovo `progid:`, může předcházet každý progid. Příklad:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Další informace o progids, naleznete [v tématu určení ID lokalizace a číslo verze](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).

   Při použití 32bitového křížového kompilátoru v 64bitovém operačním systému může kompilátor číst pouze podregistr 32bitového registru. Můžete chtít použít nativní 64bitový kompilátor k sestavení a registraci 64bitové knihovny typů.

- ID knihovny knihovny typů. Klíčové slovo `libid:`, může předcházet každé ID knihovny. Příklad:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   `version` Pokud nezadáte `lcid`nebo , [pravidla](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) použitá pro `progid:` `libid:`jsou také použita .

- Spustitelný soubor (.exe).

- Soubor knihovny (.dll) obsahující prostředek knihovny typů (například OCX).

- Složený dokument, ve který je knihovna typů.

- Jakýkoli jiný formát souboru, který lze pochopit **rozhraní loadtypelib** API.

*Atributy*\
Jeden nebo více [atributů #import](#_predir_the_23import_directive_import_attributes). Samostatné atributy mezerou nebo čárkou. Příklad:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\-nebo-

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Poznámky

### <a name="search-order-for-filename"></a><a name="_predir_the_23import_directive_searchorderforfilename"></a>Pořadí hledání pro název souboru

*název souboru* je volitelně předchází specifikace adresáře. Název souboru musí pojmenovat existující soubor. Rozdíl mezi dvěma syntaktickými formuláři je pořadí, ve kterém preprocesor hledá soubory knihovny typů, když je cesta neúplně určena.

|Formulář syntaxe|Akce|
|-----------------|------------|
|Citovaný formulář|Dá preprocesoru pokyn, aby nejprve v adresáři souboru, který obsahuje příkaz **#import,** vyhledal`#include`soubory knihovny typů a poté v adresářích libovolného souboru ( ) tohoto souboru. Preprocesor pak vyhledá v níže uvedených cestách.|
|Tvar úhlové závorky|Nastaví preprocesor, aby vyhledal soubory knihovny typů podél následujících cest:<br /><br /> 1. `PATH` Seznam cest proměnných prostředí<br />2. `LIB` Seznam cest proměnných prostředí<br />3. Cesta určená parametrem kompilátoru [/I,](../build/reference/i-additional-include-directories.md) kromě toho, že kompilátor hledá knihovnu typů, na kterou bylo odkazováno z jiné knihovny typů s atributem [no_registry.](../preprocessor/no-registry.md)|

### <a name="specify-the-localization-id-and-version-number"></a><a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>Zadejte ID lokalizace a číslo verze.

Když zadáte progid, můžete také zadat ID lokalizace a číslo verze progid. Příklad:

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Pokud ID lokalizace nezadáte, vybere se progid podle následujících pravidel:

- Pokud existuje pouze jedno ID lokalizace, používá se toto.

- Pokud existuje více než jedno ID lokalizace, použije se první s číslem verze 0, 9 nebo 409.

- Pokud existuje více než jedno ID lokalizace a žádný z nich není 0, 9 nebo 409, použije se poslední.

- Pokud nezadáte číslo verze, použije se nejnovější verze.

### <a name="header-files-created-by-import"></a><a name="_predir_the_23import_directive_header_files_created_by_import"></a>Soubory hlaviček vytvořené importem

**#import** vytvoří dva soubory hlaviček, které rekonstruují obsah knihovny typů ve zdrojovém kódu jazyka C++. Primární soubor záhlaví je podobný souboru vytvořenému kompilátorem jazyka MIDL (Microsoft Interface Definition Language), ale s dalším kódem a daty generovaným kompilátorem. [Primární soubor záhlaví](#_predir_the_primary_type_library_header_file) má stejný základní název jako knihovna typů a . Prodloužení TLH. Sekundární soubor záhlaví má stejný základní název jako knihovna typů s . Prodloužení TLI. Obsahuje implementace pro členské funkce generované kompilátorem a`#include`je zahrnut ( ) v primárním souboru záhlaví.

Pokud importujete vlastnost dispinterface, která používá `byref` parametry, **#import** negeneruje příkaz [__declspec(vlastnost)](../cpp/property-cpp.md) pro funkci.

Oba soubory hlaviček jsou umístěny ve výstupním adresáři určeném volbou [/Fo (name object file).](../build/reference/fo-object-file-name.md) Jsou pak číst a kompilovány kompilátorem, jako kdyby `#include` byl primární soubor záhlaví pojmenován direktivou.

Následující optimalizace kompilátoru jsou dodávány s **direktivou #import:**

- Soubor záhlaví, když je vytvořen, je uveden stejné časové razítko jako knihovna typů.

- Při **#import** je zpracována, kompilátor nejprve zkontroluje, zda záhlaví existuje a je aktuální. Pokud ano, pak to nemusí být znovu vytvořen.

Direktiva **#import** se také účastní minimálního sestavení a může být umístěna do předkompilovaného souboru hlaviček.  Další informace naleznete [v tématu Vytváření předkompilovaných souborů hlaviček](../build/creating-precompiled-header-files.md).

### <a name="primary-type-library-header-file"></a><a name="_predir_the_primary_type_library_header_file"></a>Soubor záhlaví knihovny primárního typu

Primární soubor záhlaví knihovny typů se skládá ze sedmi částí:

- Nadpis často používaný text: `#include` Skládá se z komentářů, prohlášení pro COMDEF. H (který definuje některá standardní makra použitá v záhlaví) a další různé informace o nastavení.

- Dopředné odkazy a typedefs: Skládá se `struct IMyInterface` z deklarací struktury, jako je například typedefs.

- Deklarace inteligentního ukazatele: `_com_ptr_t` Třída šablony je inteligentní ukazatel. Zapouzdřuje ukazatele rozhraní a eliminuje potřebu `AddRef` `Release`volat `QueryInterface` , a funkce. Také skryje `CoCreateInstance` volání při vytváření nového objektu COM. Tato část používá `_COM_SMARTPTR_TYPEDEF` příkaz makra k vytvoření typedefs rozhraní COM jako specializace šablony [_com_ptr_t](../cpp/com-ptr-t-class.md) třídy šablony. Například pro `IMyInterface`rozhraní , . TLH soubor bude obsahovat:

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   který kompilátor rozšíří na:

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   Typ `IMyInterfacePtr` pak lze použít místo ukazatele `IMyInterface*`nezpracovanérozhraní . V důsledku toho není nutné volat `IUnknown` různé členské funkce

- Typeinfo deklarace: Primárně se skládá z definice třída a další `ITypeLib:GetTypeInfo`položky vystavení jednotlivé typeinfo položky vrácené . V této části se každé informace o typech z knihovny typů `TYPEKIND` projeví v záhlaví ve formuláři závislém na informacích.

- Volitelná definice identifikátoru GUID starého stylu: Obsahuje inicializace pojmenovaných konstant GUID. Tyto názvy `CLSID_CoClass` mají `IID_Interface`formulář a , podobně jako ty generované kompilátorem MIDL.

- `#include`pro hlavičku knihovny sekundárního typu.

- Zápatí často používaný `#pragma pack(pop)`text: V současné době zahrnuje .

Všechny oddíly, s výjimkou standardního štítku a zápatí často používaný oddíl, `library` jsou uzavřeny v oboru názvů s jeho názvem určeným příkazem v původním souboru IDL. Názvy z hlavičky knihovny typů můžete použít pomocí explicitní kvalifikace pomocí názvu oboru názvů. Nebo můžete zahrnout následující příkaz:

```cpp
using namespace MyLib;
```

bezprostředně po **#import** příkazu ve zdrojovém kódu.

Obor názvů lze potlačit pomocí atributu [no_namespace](no-namespace.md)) **direktivy #import.** Potlačení oboru názvů však může vést ke kolizím názvů. Obor názvů lze také přejmenovat atributem [rename_namespace.](rename-namespace.md)

Kompilátor poskytuje úplnou cestu k libovolné závislosti knihovny typů vyžadované knihovnou typů, kterou aktuálně zpracovává. Cesta je zapsána ve formě komentářů do hlavičky knihovny typů (. TLH), který kompilátor generuje pro každou knihovnu zpracovaných typů.

Pokud knihovna typů obsahuje odkazy na typy definované v jiných knihovnách typů, pak . Soubor TLH bude obsahovat komentáře následujícího řazení:

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

Skutečný název souboru v **komentáři #import** je úplná cesta knihovny křížových odkazů typů uložená v registru. Pokud narazíte na chyby, které jsou způsobeny chybějící definice typu, zkontrolujte komentáře v čele . TLH zobrazíte, které závislé knihovny typů může být nutné importovat jako první. Pravděpodobné chyby jsou syntaktické chyby (například C2143, C2146, C2321), C2501 (chybějící specifikátory decl) nebo C2433 ("inline" není povoleno na deklaraci dat) při kompilaci . TLI.

Chcete-li vyřešit chyby závislostí, určete, které komentáře závislostí nejsou jinak poskytovány systémovými hlavičkami, a poté zadejte **#import** direktivu v určitém okamžiku před **#import** direktivou závislé knihovny typů.

### <a name="import-attributes"></a><a name="_predir_the_23import_directive_import_attributes"></a>#import atributy

**#import** mohou volitelně obsahovat jeden nebo více atributů. Tyto atributy sdělují kompilátoru, aby upravil obsah záhlaví knihovny typů. Symbol zpětného**\\**lomítka ( ) lze použít k zahrnutí dalších řádků do jednoho **příkazu #import.** Příklad:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Další informace naleznete [v tématu #import atributy](../preprocessor/hash-import-attributes-cpp.md).

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[Směrnice preprocesoru](../preprocessor/preprocessor-directives.md)\
[Podpora com kompilátoru](../cpp/compiler-com-support.md)
