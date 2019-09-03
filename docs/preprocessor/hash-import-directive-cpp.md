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
ms.openlocfilehash: afd05e7380ec3838fe9763be23ccfae338adb4fb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220264"
---
# <a name="import-directive-c"></a>#import direktivaC++()

**C++Konkrétní**

Slouží k začleňování informací z knihovny typů. Obsah knihovny typů je převeden na C++ třídy, převážně popisující rozhraní modelu COM.

## <a name="syntax"></a>Syntaxe

> **#import** *atributy* *filename* \[] \
> **#import** *atributy filename*]> \[ \<

### <a name="parameters"></a>Parametry

*Bitmap*\
Určuje knihovnu typů, která se má importovat. *Název souboru* může být jeden z následujících typů:

- Název souboru, který obsahuje knihovnu typů, například soubor. olb,. tlb nebo. dll. Klíčové slovo `file:`může předcházet každý název souboru.

- Identifikátor ProgID ovládacího prvku v knihovně typů. Klíčové slovo `progid:`může předcházet každému identifikátoru ProgID. Příklad:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Další informace o identifikátorech ProgID naleznete v tématu [Určení ID lokalizace a čísla verze](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).

   Při použití 32ho křížového kompilátoru na 64 operačním systému může kompilátor přečíst pouze podregistr 32 bitových procesorů. Můžete chtít použít nativní kompilátor 64 k sestavení a registraci knihovny typů 64.

- ID knihovny typů Klíčové slovo `libid:`může předcházet každé ID knihovny. Příklad:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   Pokud nezadáte `version` `lcid`nebo, `progid:` uplatní [](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) setakypravidlapoužitá`libid:`pro.

- Spustitelný soubor (. exe).

- Soubor knihovny (. dll) obsahující prostředek knihovny typů (například. ocx).

- Složený dokument držící knihovnu typů.

- Jakýkoli jiný formát souboru, který může pochopit rozhraní **LoadTypeLib** API.

*atribut*\
Jeden nebo více [atributů #import](#_predir_the_23import_directive_import_attributes). Jednotlivé atributy oddělujte mezerou nebo čárkou. Příklad:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\-ani

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Poznámky

### <a name="_predir_the_23import_directive_searchorderforfilename"></a>Pořadí hledání názvu souboru

*název souboru* je volitelně uveden v adresáři specifikace. Název souboru musí pojmenovat existující soubor. Rozdíl mezi dvěma formami syntaxe je pořadí, ve kterém preprocesor hledá soubory knihovny typů, pokud je cesta zadána neúplně.

|Forma syntaxe|Akce|
|-----------------|------------|
|Citovaný formulář|Vydá pokyn preprocesoru, aby nejprve hledal soubory knihovny typů v adresáři souboru, který obsahuje příkaz **#import** a potom v adresářích libovolného souboru include (`#include`) Tento soubor. Preprocesor pak vyhledá podél cest, které jsou uvedeny níže.|
|Formulář lomené závorky|Vydá pokyn preprocesoru k hledání souborů knihovny typů na následujících cestách:<br /><br /> 1.  Seznam `PATH` cest k proměnným prostředí<br />2.  Seznam `LIB` cest k proměnným prostředí<br />3.  Cesta zadaná v možnosti kompilátoru [/i](../build/reference/i-additional-include-directories.md) , s výjimkou toho, že kompilátor hledá knihovnu typů, na kterou se odkazuje z jiné knihovny typů s atributem [no_registry](../preprocessor/no-registry.md) .|

### <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>Zadejte ID lokalizace a číslo verze

Když zadáte ProgID, můžete také zadat ID lokalizace a číslo verze ProgID. Příklad:

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Pokud nezadáte ID lokalizace, je identifikátor ProgID zvolen podle následujících pravidel:

- Pokud je k dispozici pouze jedno ID lokalizace, bude použito.

- Pokud je k dispozici více než jeden identifikátor lokalizace, použije se první z nich s číslem verze 0, 9 nebo 409.

- Pokud je k dispozici více než jeden identifikátor lokalizace a žádná z nich není 0, 9 nebo 409, použije se poslední z nich.

- Pokud nezadáte číslo verze, použije se nejnovější verze.

###  <a name="_predir_the_23import_directive_header_files_created_by_import"></a>Soubory hlaviček vytvořené importem

**#import** vytvoří dva soubory hlaviček, které rekonstruuje obsah knihovny typů ve C++ zdrojovém kódu. Primární hlavičkový soubor je podobný jako ten vytvořený kompilátorem MIDL (Microsoft Interface Definition Language), ale s dalším kódem generovaným kompilátorem a daty. [Primární hlavičkový soubor](#_predir_the_primary_type_library_header_file) má stejný základní název jako knihovna typů a. Rozšíření TLH. Sekundární hlavičkový soubor má stejný základní název jako knihovna typů s příponou. Rozšíření TLI. Obsahuje implementace pro členské funkce generované kompilátorem a je obsažen (`#include`) v primárním souboru hlaviček.

Pokud importujete vlastnost odesílajícího typu, `byref` která používá parametry, **#import** negeneruje příkaz [__declspec (Property)](../cpp/property-cpp.md) pro funkci.

Oba hlavičkové soubory jsou umístěny ve výstupním adresáři určeném možností [/FO (název objektového souboru)](../build/reference/fo-object-file-name.md) . Pak jsou čteny a kompilovány kompilátorem, jako by byl primární hlavičkový soubor pojmenován `#include` direktivou.

Následující optimalizace kompilátoru jsou dodávány s direktivou **#import** :

- Hlavičkový soubor, když je vytvořen, má stejné časové razítko jako knihovna typů.

- Při zpracování **#import** kompilátor nejprve zkontroluje, zda hlavička existuje a je aktuální. Pokud ano, pak se nemusí znovu vytvořit.

Direktiva **#import** se také účastní minimálního opětovného sestavení a lze ji umístit do souboru předkompilované hlavičky.  Další informace naleznete v tématu [vytváření předkompilovaných hlavičkových souborů](../build/creating-precompiled-header-files.md).

### <a name="_predir_the_primary_type_library_header_file"></a>Hlavičkový soubor primární knihovny typů

Soubor hlaviček primární knihovny typů se skládá ze sedmi částí:

- Často používaný text nadpisu: Sestává z komentářů `#include` , příkazů pro Comdef. H (definuje některá standardní makra použitá v hlavičce) a další informace o nastavení.

- Dopředné odkazy a definice typedef: Se skládá z deklarací struktury, `struct IMyInterface` jako jsou a definice typedef.

- Deklarace inteligentního ukazatele: Třída `_com_ptr_t` šablony je inteligentní ukazatel. Zapouzdřuje ukazatele rozhraní a eliminuje nutnost volání `AddRef`funkcí, `Release`a `QueryInterface` . Také skryje `CoCreateInstance` volání při vytváření nového objektu com. V této části se používá příkaz `_COM_SMARTPTR_TYPEDEF` makra k navázání definice typedef rozhraní COM jako specializace šablony třídy šablony [_com_ptr_t](../cpp/com-ptr-t-class.md) . Například pro rozhraní `IMyInterface`,. Soubor TLH bude obsahovat:

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   který kompilátor bude rozšířen na:

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   Typ `IMyInterfacePtr` se pak dá použít místo ukazatele `IMyInterface*`nezpracovaného rozhraní. V důsledku toho není nutné volat různé `IUnknown` členské funkce

- Deklarace TypeInfo: Primárně se skládá z definic tříd a dalších položek, které zpřístupňují jednotlivé položky TypeInfo `ITypeLib:GetTypeInfo`vrácené funkcí. V této části se každé volání TypeInfo z knihovny typů odráží v záhlaví na formuláři závislém na těchto `TYPEKIND` informacích.

- Volitelná definice GUID starého stylu: Obsahuje inicializace pojmenovaných konstant GUID. Tyto názvy mají formulář `CLSID_CoClass` a `IID_Interface`jsou podobné těm, které jsou generovány kompilátorem MIDL.

- `#include`příkaz pro záhlaví sekundární knihovny typů

- Často používaný text zápatí: V současné `#pragma pack(pop)`době zahrnuje.

Všechny oddíly s výjimkou často používaného textu nadpisu a často používaného oddílu zápatí jsou uzavřeny v oboru názvů `library` s názvem zadaným příkazem v původním souboru IDL. Názvy z hlavičky knihovny typů můžete použít explicitní kvalifikací pomocí názvu oboru názvů. Nebo můžete zahrnout následující příkaz:

```cpp
using namespace MyLib;
```

ihned po příkazu **#import** ve zdrojovém kódu.

Obor názvů lze potlačit pomocí atributu [no_namespace](no-namespace.md)) direktivy **#import** . Nicméně potlačení oboru názvů může vést k kolizím názvů. Obor názvů lze také přejmenovat pomocí atributu [rename_namespace](rename-namespace.md) .

Kompilátor poskytuje úplnou cestu k jakékoli závislosti knihovny typů vyžadované knihovnou typů, kterou právě zpracovává. Cesta je zapsána ve formě komentářů do hlavičky knihovny typů (. TLH), který kompilátor generuje pro každou zpracovávanou knihovnu typů.

Pokud knihovna typů obsahuje odkazy na typy definované v jiných knihovnách typů, pak. Soubor TLH bude obsahovat komentáře následujícího řazení:

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

Skutečný název souboru v komentáři **#import** je úplná cesta knihovny typů křížového odkazu, jak je uložena v registru. Pokud dojde k chybám, které jsou způsobeny chybějícími definicemi typu, podívejte se na komentáře v záhlaví. TLH, abyste viděli, které závislé knihovny typů možná budete muset nejdřív naimportovat. Pravděpodobnými chybami jsou chyby syntaxe (například C2143, C2146, C2321), C2501 (chybějící specifikátory), nebo C2433 (' inline ' není pro deklaraci dat povoleno) při kompilování. Soubor TLI

Chcete-li vyřešit chyby závislostí, určete, které z komentářů závislosti nejsou jinak poskytovány systémovými hlavičkami, a pak zadejte **#import** direktivu v určitém bodě před direktivou **#import** závislé knihovny typů.

### <a name="_predir_the_23import_directive_import_attributes"></a>Atributy #import

**#import** může volitelně zahrnovat jeden nebo více atributů. Tyto atributy říká kompilátoru, aby upravil obsah hlaviček knihovny typů. Symbol zpětného lomítka ( **\\** ) lze použít k zahrnutí dalších řádků do jednoho příkazu **#import** . Příklad:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Další informace najdete v tématu [#import atributy](../preprocessor/hash-import-attributes-cpp.md).

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)\
[Podpora kompilátoru COM](../cpp/compiler-com-support.md)
