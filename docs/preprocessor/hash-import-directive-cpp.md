---
title: '#Import – direktiva (C++) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#import'
dev_langs:
- C++
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19dcd538556db4efc378853c929aa1cf69905037
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808521"
---
# <a name="import-directive-c"></a>#import – direktiva (C++)

**Specifické pro C++**

Používá se k opatření informací z knihovny typů. Obsah knihovny typů je převeden na třídy jazyka C++, převážně popisující rozhraní COM.

## <a name="syntax"></a>Syntaxe

```
#import "filename" [attributes]
#import <filename> [attributes]
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Určuje knihovnu typů pro import. *Název souboru* může být jedna z následujících akcí:

- Název souboru obsahujícího knihovnu typů, jako je například soubor olb, TLB nebo DLL. Klíčové slovo **souboru:**, může předcházet každý název souboru.

- Progid ovládacího prvku v knihovně typů. Klíčové slovo **progid:**, může předcházet každý parametr progid. Příklad:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Další informace o identifikátorech ProgID, viz [určení ID lokalizace a číslo verze](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).

   Všimněte si, že při kompilaci s křížovým kompilátorem v operačním systému 64-bit kompilátor bude moct číst pouze 32bitové podregistru. Můžete chtít používat nativní 64bitový kompilátor pro sestavení a registrací knihovny 64bitového typu.

- ID knihovny knihovny typů. Klíčové slovo **libid:**, může předcházet každé ID knihovny. Příklad:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   Pokud neurčíte verzi nebo lcid, [pravidla](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) , která jsou použita na **progid:** platí také pro **libid:**.

- Soubor spustitelný soubor (.exe).

- Soubor knihovny (DLL) obsahující zdroj knihovny typů (například ocx).

- Složený dokument s knihovnou typů.

- Další formáty souborů, který může být srozumitelné **LoadTypeLib** rozhraní API.

*Atributy*<br/>
Jeden nebo více [atributů #import](#_predir_the_23import_directive_import_attributes). Samostatné atributy s mezerami nebo čárkami. Příklad:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\-nebo –

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Poznámky

## <a name="_predir_the_23import_directive_searchorderforfilename"></a> Pořadí hledání názvů souborů

*Název souboru* může volitelně předcházet specifikace adresáře. Název souboru musí být název existujícího souboru. Rozdíl mezi dvě různými formami syntaxe je v tom pořadí, ve kterém preprocesor hledá soubory s knihovnami typu případě je cesta zadána neúplně.

|Forma syntaxe|Akce|
|-----------------|------------|
|Citovaný formulář|Vydá pokyn preprocesoru k vyhledání typu souborů knihoven v adresáři souboru, který obsahuje první **#import** příkaz a poté v adresářích s ostatními soubory, které zahrnují (`#include`) tohoto souboru. Preprocesor pak bude hledat podél cest, které je uvedeno níže.|
|Forma lomené závorky|Vydá pokyn preprocesoru k vyhledání typu souborů knihoven v následujících umístěních:<br /><br /> 1.  `PATH` Seznam proměnných cest prostředí<br />2.  `LIB` Seznam proměnných cest prostředí<br />3.  Cestu určenou položkou /I (Další adresáře souborů k zahrnutí) – možnost kompilátoru, kromě toho kompilátor bude hledat knihovnu typů, která byla popsána z jiné knihovny typů s [no_registry s: %](../preprocessor/no-registry.md) atribut.|

##  <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a> Určení ID lokalizace a číslo verze

Při zadávání progid můžete také zadat číslo ID a verzi lokalizace ProgID. Příklad:

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Pokud není zadán Identifikátor lokalizace, progid je zvolena podle následujících pravidel:

- Pokud existuje pouze jedno ID lokalizace, používá se.

- Pokud existuje více než jeden ID lokalizace, použije se ten první s číslem verze 0, 9 nebo 409.

- Pokud existuje více než jeden ID lokalizace a žádný z nich není 0, 9 nebo 409, použije se ten poslední.

- Pokud nezadáte číslo verze, použije se nejnovější verzi.

##  <a name="_predir_the_23import_directive_header_files_created_by_import"></a> Hlavičkové soubory vytvořené pomocí importu

**#import** vytvoří dva soubory hlaviček, které rekonstruují obsah knihovny typů ve zdrojovém kódu C++. Primární soubor záhlaví je podobný vyrobenému pomocí kompilátoru Microsoft Interface Definition Language (MIDL), ale s další kód generovaný kompilátorem a daty. [Primární soubor záhlaví](#_predir_the_primary_type_library_header_file) má stejný základní název knihovna typů navíc. TLH rozšíření. Sekundární záhlaví souboru má stejný základní název knihovna typů, se. Rozšíření TLI. Obsahuje implementace pro kompilátorem generované členské funkce a je součástí (`#include`) v primárním souboru záhlaví.

Pokud importujete vlastnost dispinterface, která používá parametr ByRef, #import nevygeneruje __declspec ([vlastnost](../cpp/property-cpp.md)) příkaz pro funkci.

Oba hlavičkové soubory jsou umístěny ve výstupním adresáři určeném možností /Fo (název souboru objektu). Jsou pak čteny a zkompilovány kompilátorem, jako by byl soubor primárního záhlaví pojmenován podle `#include` směrnice.

Součástí následující optimalizace kompilátoru **#import** – direktiva:

- Soubor s hlavičkou má při vytvoření, dostane stejné časové razítko jako knihovny typů.

- Když **#import** je zpracována, kompilátor nejprve zkontroluje, zda záhlaví existuje a je aktuální. Pokud ano, pak nemusí být znovu vytvořen.

**#Import** – direktiva také účastní minimálního opětovného sestavení a je možné použít v souboru předkompilované hlavičky. Zobrazit [vytváření předkompilovaných hlavičkových souborů](../build/reference/creating-precompiled-header-files.md) Další informace.

###  <a name="_predir_the_primary_type_library_header_file"></a> Hlavičkový soubor primární typ knihovny
Hlavičkový soubor primární typ knihovny se skládá ze sedmi částí:

- Nadpisu: tvořen komentáři, `#include` příkaz pro COMDEF. H (definující některá standardní makra použitá v záhlaví) a další informace o.

- Dopředné odkazy a funkce TypeDef: se skládá ze struktur deklarací jako `struct IMyInterface` a definice TypeDef.

- Deklarace inteligentního ukazatele: třída šablony `_com_ptr_t` implementaci inteligentního ukazatele, který zapouzdřuje ukazatele rozhraní a eliminuje nutnost volání `AddRef`, `Release`, `QueryInterface` funkce. Navíc skryje `CoCreateInstance` volat při vytváření nového objektu COM. Tento oddíl používá příkaz Makro `_COM_SMARTPTR_TYPEDEF` k vytvoření funkcí TypeDef rozhraní modelu COM, aby byly specializovanými z [_com_ptr_t](../cpp/com-ptr-t-class.md) šablony třídy. Například pro rozhraní `IMyInterface`,. TLH soubor bude obsahovat:

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   který kompilátor bude rozbalen do:

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   Typ `IMyInterfacePtr` můžete použít namísto nezpracovaného ukazatele rozhraní `IMyInterface*`. V důsledku toho není nutné volat různé `IUnknown` členské funkce

- Deklarace TypeInfo: primárně se skládá z definic tříd a ostatních položek vystavovaných individuálním položkám typeinfo vrácených `ITypeLib:GetTypeInfo`. V této části se každá vlastnost typeinfo z knihovny typů odráží v záhlaví ve formě závislé na `TYPEKIND` informace.

- Volitelné definice GUID starého stylu: obsahuje inicializaci pojmenovaných konstant identifikátoru GUID. Jedná se o názvy formuláře `CLSID_CoClass` a `IID_Interface`, podobné těm, které jsou generovány v kompilátoru MIDL.

- `#include` příkaz pro sekundární hlavičku knihovny typů.

- Často používaný text zápatí: nyní zahrnuje `#pragma pack(pop)`.

Všechny oddíly s výjimkou záhlaví často používaný text zápatí často používaný text části a jsou uzavřeny v oboru názvů určeném podle `library` příkaz v původním souboru IDL. Můžete použít názvy v záhlaví typu knihovny k explicitní kvalifikaci s oborem názvů nebo zahrnutím následujícího příkazu:

```cpp
using namespace MyLib;
```

ihned po **#import** příkaz ve zdrojovém kódu.

Obor názvů lze potlačit pomocí [no_namespace](#_predir_no_namespace) atribut **#import** směrnice. Nicméně potlačení oboru názvů může vést ke kolizi názvů. Obor názvů můžete také přejmenovat [rename_namespace](#_predir_rename_namespace) atribut.

Kompilátor poskytuje úplnou cestu k libovolné závislosti knihovny typu vyžadované, kterou právě zpracovávaná knihovna typů. Cesta je zapsána ve formě komentářů do záhlaví typu knihovny (. TLH), kompilátor generuje pro každou zpracovanou knihovnu typů.

Pokud knihovna typů obsahuje odkazy na typy definované v jiných knihovnách typů, pak bude. TLH soubor obsahovat komentáře následujícího druhu:

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

Skutečný název souboru **#import** komentář je úplná cesta knihovny typů s křížovými odkazy, jak je uložen v registru. Pokud narazíte na chyby, které jsou z důvodu chybějící definice typu, zkontrolujte poznámky v čele. TLH zobrazíte závislé knihovny typů pravděpodobně nutné nejprve importovat. Pravděpodobné chyby jsou chyby syntaxe (například C2143, C2146, C2321), C2501 (chybí specifikátory decl) nebo C2433 ("vložené" nejsou u dat deklarace povoleny) při kompilaci. Souboru TLI.

Musíte určit, které závislosti komentáře nejsou jinak poskytovány pro záhlaví systému a pak zadejte **#import** direktiv v určitém okamžiku před **#import** direktiv závislé osoby. knihovny typů na případné chyby opravte.

## <a name="_predir_the_23import_directive_import_attributes"></a> atributů #import

**#import** může volitelně zahrnovat jeden nebo více atributů. Tyto atributy oznamují kompilátoru, který chcete upravit obsah záhlaví knihovny typů. Zpětné lomítko (**\\**) symbolů lze použít k zahrnutí dalších řádků do jediného **#import** příkazu. Příklad:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Další informace najdete v tématu [atributů #import](../preprocessor/hash-import-attributes-cpp.md).

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)<br/>
[Podpora kompilátoru COM](../cpp/compiler-com-support.md)