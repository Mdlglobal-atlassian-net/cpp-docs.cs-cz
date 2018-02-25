---
title: "#Import – direktiva (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cbf8a35022638884733f5151fffb2a3a0a2946c3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="import-directive-c"></a>#import – direktiva (C++)
**Konkrétní C++**  
  
 Umožňuje začlenit informace z knihovny typů. Obsah knihovny typů jsou převedeny do třídy C++, většinou popisující rozhraní COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#import "filename" [attributes]  
#import <filename> [attributes]  
```  
  
#### <a name="parameters"></a>Parametry  
 *filename*  
 Určuje typ knihovny pro import. `filename` Může být jedna z následujících akcí:  
  
-   Název souboru, který obsahuje knihovny typů, jako je například soubor .olb, .tlb nebo .dll. Klíčové slovo, **souboru:**, lze předcházet každý název souboru.  
  
-   Progid v knihovně typu ovládacího prvku. Klíčové slovo, **progid:**, lze předcházet každý progid. Příklad:  
  
    ```  
    #import "progid:my.prog.id.1.5"  
    ```  
  
     Další informace o ID programů, najdete v části [zadáte ID lokalizace a číslo verze](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).  
  
     Všimněte si, že když kompilujete s křížové kompilátoru na 64bitový operační systém, kompilátor bude moct číst pouze 32bitové podregistru. Můžete chtít použít nativní 64bitový kompilátor pro sestavení a registraci knihovny typů 64-bit.  
  
-   ID knihovny knihovny typů. Klíčové slovo, **ID knihovny:**, lze předcházet každé ID knihovny. Příklad:  
  
    ```  
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")  
    ```  
  
     Pokud nezadáte verze nebo lcid, [pravidla](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) , se použijí pro **progid:** , použijí se **ID knihovny:**.  
  
-   Soubor spustitelný soubor (.exe).  
  
-   Soubor knihovny (DLL.dll) obsahující prostředek knihovny typů (například .ocx).  
  
-   Složené dokument, který uchovává knihovny typů.  
  
-   Všechny ostatní formát souboru, který může být srozumitelné **LoadTypeLib** rozhraní API.  
  
 `attributes`  
 Jeden nebo více [#import – atributy](#_predir_the_23import_directive_import_attributes). Samostatné atributy s mezerami nebo čárkami. Příklad:  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only  
```  
  
 -nebo-  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only  
```  
  
## <a name="remarks"></a>Poznámky  
  
##  <a name="_predir_the_23import_directive_searchorderforfilename"></a> Pořadí vyhledávání pro název souboru  
 *Název souboru* volitelně předchází specifikaci adresáře. Název existující soubor musí být název souboru. Rozdíl mezi dvě různé formy je v pořadí, ve kterém preprocesor vyhledá soubory knihovny typu-li úplně zadána cesta.  
  
|Syntaxe formuláře|Akce|  
|-----------------|------------|  
|Uvozovkách formuláře|Dá pokyn preprocesor hledání souborů knihovny typ nejprve v adresáři souboru, který obsahuje `#import` příkaz a potom v adresáři jakékoli soubory, které zahrnují (`#include`) souboru. Preprocesor pak prohledá podél cesty vidíte níže.|  
|Formulář ostré závorky|Dá pokyn preprocesor hledání souborů knihovny typu podél následující cesty:<br /><br /> 1.  **Cesta** seznamu cest proměnné prostředí<br />2.  **LIB** seznamu cest proměnné prostředí<br />3.  Cestu určenou položkou /I (Další adresáře souborů k zahrnutí) – možnost kompilátoru, s výjimkou ho kompilátor hledá knihovny typů, který se odkazuje z jiného typu knihovny se [no_registry –](../preprocessor/no-registry.md) atribut.|  
  
##  <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a> Lokalizace ID a číslo verze  
 Když zadáte progid, můžete také zadat lokalizace ID a verzi počet progid. Příklad:  
  
```  
#import "progid:my.prog.id" lcid("0") version("4.0)  
```  
  
 Pokud nezadáte ID lokalizace, progid je zvolen podle následujících pravidel:  
  
-   Pokud existuje jenom jeden lokalizace ID, než se používá.  
  
-   Pokud existuje více než jeden lokalizace ID, použije se první z nich s číslem verze, 0, 9 nebo 409.  
  
-   Pokud existuje více než jedno ID lokalizace a žádný z nich jsou 0, 9 nebo 409, použije se poslední.  
  
-   Pokud nezadáte číslo verze, použije se nejnovější verzi.  
  
##  <a name="_predir_the_23import_directive_header_files_created_by_import"></a> Soubory hlaviček vytvořené importu  
 `#import` vytvoří dvě hlavičky souborů, které rekonstrukci obsah knihovny typu ve zdrojovém kódu C++. Primární záhlaví souboru je podobná vytvořeného kompilátorem Microsoft rozhraní Definition Language (MIDL), ale s další generované kompilátorem kód a data. [Primární hlavičkový soubor](#_predir_the_primary_type_library_header_file) má stejný název základní jako knihovny typů, plus. TLH rozšíření. Sekundární hlavičkový soubor má stejný název základní jako knihovny typů s. TLI rozšíření. Obsahuje implementace pro generované kompilátorem členských funkcí a je součástí (`#include`) v primární záhlaví souboru.  
  
 Importování dispinterface vlastnost, která používá byref parametry, #import nevygeneruje __declspec ([vlastnost](../cpp/property-cpp.md)) příkaz pro funkci.  
  
 Oba soubory hlaviček ukládány do výstupního adresáře určeného parametrem /Fo (název souboru objektů). Jsou pak číst a kompilovány pomocí kompilátoru, jako kdyby byl název souboru primární záhlaví `#include` – direktiva.  
  
 Následující optimalizace kompilátoru jsou součástí `#import` – direktiva:  
  
-   Soubor hlaviček, při vytváření, dostane stejné časové razítko jako knihovny typů.  
  
-   Když `#import` je zpracování kompilátor nejprve zkontroluje, zda záhlaví existuje a zda je aktuální. Pokud ano, pak nemusí být znovu vytvořena.  
  
 `#import` – Direktiva také účastní minimální opětovné sestavení a mohou být umístěny v předkompilovaný hlavičkový soubor. V tématu [vytváření předkompilovaných hlavičkových souborů](../build/reference/creating-precompiled-header-files.md) Další informace.  
  
###  <a name="_predir_the_primary_type_library_header_file"></a> Hlavičkový soubor knihovny primární typů  
 Hlavičkový soubor knihovny primární typů se skládá ze sedmi částech:  
  
-   Záhlaví standardní: se skládá z komentáře `#include` příkaz pro COMDEF. H (který definuje některé standardní makra použít v záhlaví) a dalších informací o ostatní nastavení.  
  
-   Předávání odkazy a definice TypeDef: se skládá z deklarace struktur, jako `struct IMyInterface` a definice TypeDef.  
  
-   Inteligentní deklarace ukazatelů: šablony třídy `_com_ptr_t` je implementace čipové ukazatele, který zapouzdřuje ukazatele rozhraní a eliminuje nutnost volání `AddRef`, **verze**, `QueryInterface` funkce. Kromě toho skryje `CoCreateInstance` volání při vytváření nového objektu COM. Tato část používá příkaz Makro **_COM_SMARTPTR_TYPEDEF** k vytvoření definice TypeDef rozhraní modelu COM, jako šablona specializací [_com_ptr_t –](../cpp/com-ptr-t-class.md) třídy šablony. Například pro rozhraní **IMyInterface**,. TLH soubor bude obsahovat:  
  
    ```  
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
    ```  
  
     které kompilátor bude rozbalit na:  
  
    ```  
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;  
    ```  
  
     Typ `IMyInterfacePtr` pak jde použít místo ukazatel nezpracovaná rozhraní `IMyInterface*`. V důsledku toho není nutné volat různé **IUnknown** členské funkce  
  
-   TypeInfo – deklarace: především se skládá z definice tříd a dalším položkám vystavení TypeInfo – jednotlivých položek vrácených **ITypeLib:GetTypeInfo**. V této části se projeví každý TypeInfo – z knihovny typů v hlavičce v závisí na formuláři `TYPEKIND` informace.  
  
-   Volitelný GUID definice starého: obsahuje inicializacích pojmenované konstanty identifikátor GUID. Toto jsou názvy ve formátu **CLSID_CoClass** a **IID_Interface**, podobné těm, které jsou generované kompilátorem MIDL.  
  
-   `#include` příkaz pro hlavičku sekundární typ knihovny.  
  
-   Standardní zápatí: aktuálně zahrnuje `#pragma pack(pop)`.  
  
 Všechny oddíly, s výjimkou záhlaví standardní zápatí standardní části a jsou uzavřené v oboru názvů s názvem určeného **knihovny** příkaz v původní soubor IDL. Názvy z hlavičky typu knihovny můžete použít explicitní kvalifikace názvu oboru názvů nebo zahrnutím následující příkaz:  
  
```  
using namespace MyLib;  
```  
  
 ihned po `#import` příkaz ve zdrojovém kódu.  
  
 Obor názvů lze potlačit pomocí [no_namespace –](#_predir_no_namespace) atribut `#import` – direktiva. Však potlačení obor názvů může vést k kolize názvů. Obor názvů lze také přejmenovat pomocí [rename_namespace –](#_predir_rename_namespace) atribut.  
  
 Kompilátor poskytuje úplnou cestu k některé závislé knihovny typu vyžadují knihovny typů, které se právě zpracovává. Cesta k zápisu, ve formě komentářů, do záhlaví typu knihovny (. TLH), kompilátor generuje pro každou zpracovat knihovny typů.  
  
 Pokud knihovny typů obsahuje odkazy na typy definované v jiné knihovny typů, pak se. TLH soubor bude obsahovat komentář řazení následující:  
  
```  
//  
// Cross-referenced type libraries:  
//  
//  #import "c:\path\typelib0.tlb"  
//  
```  
  
 Skutečný název souboru v `#import` komentář je úplná cesta knihovny referencí typů, jak je uložen v registru. Pokud narazíte na chyby, které jsou z důvodu chybějícího definice typů, zkontrolujte komentáře v první pozice. TLH zobrazíte které závislého typu knihovny možná muset být nejprve importovány. Chyby syntaxe (například C2143, C2146, C2321), jsou nejspíš chyby C2501 (chybějící decl specifikátory), nebo C2433 ('vložené' není povolený v deklaraci data) při kompilování. TLI soubor.  
  
 Můžete třeba zjistit, který závislosti komentáře, jinak neupravují hlavičky systému a pak zadejte `#import` direktivy v určitém okamžiku před `#import` direktivy knihovny závislého typu případné chyby opravte.  
  
 Další informace najdete v článku znalostní báze Knowledge Base "#import obálku metod může způsobit narušení přístupu" (Q242527) nebo "chyby kompilátoru při použití #import se souborem XML" (Q269194). Můžete najít články znalostní báze Knowledge Base na médiu knihovny MSDN nebo v [Microsoft Support](https://support.microsoft.com/).  
  
##  <a name="_predir_the_23import_directive_import_attributes"></a> #import – atributy  
 `#import` může volitelně obsahovat jeden nebo více atributů. Tyto atributy oznámení kompilátoru změnit obsah hlavičky knihovny typů. Zpětné lomítko (**\\**) symbol je možné zahrnout další řádky v jediném `#import` příkaz. Příklad:  
  
```  
#import "test.lib" no_namespace \  
   rename("OldName", "NewName")  
```  
  
 Další informace najdete v tématu [#import – atributy](../preprocessor/hash-import-attributes-cpp.md).  
  
 Konkrétní END C++  
  
## <a name="see-also"></a>Viz také  
 [Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)   
 [Podpora kompilátoru COM](../cpp/compiler-com-support.md)
