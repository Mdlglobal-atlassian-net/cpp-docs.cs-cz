---
title: Chyba linkerů Lnk2005 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2005
dev_langs:
- C++
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f853bec220c7d46ed2a0c44ac1e1d45fbca8318f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301239"
---
# <a name="linker-tools-error-lnk2005"></a>Chyba linkerů LNK2005
*symbol* již definována v objektu  
  
Symbol *symbol* byl definován více než jednou.   
  
Tato chyba je následován závažná chyba [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).  
  
### <a name="possible-causes-and-solutions"></a>Možné příčiny a řešení  
  
Obecně platí, tato chyba znamená, mají poškozen *jednu definici pravidla*, což umožňuje jenom jednu definici pro použité šablony, funkce, typ nebo objekt v souboru daného objektu a pouze jednu definici napříč celou spustitelný soubor pro externě zobrazené objekty nebo funkce.  
  
Tady jsou některé běžné příčiny této chyby.  
  
-   Této chybě může dojít, pokud soubor hlaviček definuje proměnnou. Například pokud zahrnete více než jeden zdrojový soubor tento soubor hlaviček v projektu, vrátí chybu:  
  
    ```h  
    // LNK2005_global.h  
    int global_int;  // LNK2005
    ```  
  
    Možná řešení patří:  
  
    -   Deklarovat proměnnou `extern` v záhlaví souboru: `extern int global_int;`, pak je definujte a volitelně provést jeho inicializaci v jediném zdrojový soubor: `int global_int = 17;`. Tato proměnná je nyní globální konfiguraci, můžete použít v jakékoli zdrojový soubor deklarací `extern`, například zahrnutím soubor hlaviček. Doporučujeme, abyste toto řešení pro proměnné, které musí být globální, ale dobrý inženýrství softwaru postup minimalizuje globální proměnné.  
    
    -   Deklarovat proměnnou [statické](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;`. Omezuje oboru definice aktuální objekt souboru a umožňuje více souborů objekt má své vlastní kopie proměnnou. Není doporučeno, že definujete statické proměnné v hlavičkových souborů z důvodu nedorozuměním s globální proměnné. Přednost přesunout statické proměnné definice do zdrojových souborů, které je používají.  
  
    -   Deklarovat proměnnou [selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`. Tato hodnota informuje linkeru a vyberte jednu definici pro použití ve všech externích odkazů a vyřadí zbývající. Toto řešení je užitečné, někdy při kombinování knihoven importovat. Jinak nedoporučujeme ji jako způsob, jak se vyhnout se chybám linkeru.  
  
-   K této chybě může dojít, když soubor hlaviček definuje funkci, která není `inline`. Pokud tento soubor hlaviček zahrnete do více než jeden zdrojový soubor, získáte více definice funkce v spustitelný soubor.  
    
    ```h  
    // LNK2005_func.h  
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```  
  
    Možná řešení patří:  
  
    -   Přidat `inline` – klíčové slovo funkce: 

        ```h  
        // LNK2005_func_inline.h  
        inline int sample_function(int k) { return 42 * (k % 167); }  
        ```  
  
    -   Odeberte tělo funkce z hlavičky souboru a ponechat jenom deklarace a pak implementovat funkce v jediném zdrojového souboru:  
  
        ```h  
        // LNK2005_func_decl.h  
        int sample_function(int);  
        ```  
  
        ```cpp  
        // LNK2005_func_impl.cpp  
        int sample_function(int k) { return 42 * (k % 167); }  
        ```  
-   Této chybě může dojít také při definování členské funkce mimo deklaraci třídy v záhlaví souboru:  
  
    ```h  
    // LNK2005_member_outside.h  
    class Sample {
    public:
        int sample_function(int);  
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```  
  
    Chcete-li tento problém vyřešit, přesuňte definice funkcí člen uvnitř třídy. Členské funkce definované uvnitř deklaraci třídy jsou implicitně vložená.  
  
    ```h  
    // LNK2005_member_inline.h  
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }  
    };
    ```  
  
-   Této chybě může dojít, pokud jste více než jedna verze standardní knihovny nebo CRT. Například pokud se pokusíte maloobchodní a knihovny ladění CRT i statické a dynamické verze knihovny nebo dvě různé verze standardní knihovny propojit váš spustitelný soubor, tato chyba se může hlásit mnohokrát. Chcete-li tento problém vyřešit, odeberte všechny kromě jednoho kopírování jednotlivých knihoven z příkaz odkaz. Nedoporučujeme kombinovat maloobchodní a ladění knihoven nebo různé verze knihovny, ve stejném spustitelný soubor.  
  
    Říct linkeru používat knihovny než výchozí hodnoty, na příkazovém řádku zadejte knihovny, které chcete použít a použít [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) možnost zakázat výchozí knihovny. V prostředí IDE, přidáte odkazy na projekt k určení knihovny, které chcete použít a pak otevřete **stránky vlastností** dialogové okno pro svůj projekt a v **Linkeru**, **vstup** vlastnost Nastavte buď **ignorovat všechny výchozí knihovny**, nebo **ignorovat konkrétní výchozí knihovny** vlastnosti, které chcete zakázat výchozí knihovny.   
  
-   Této chybě může dojít, pokud zároveň použití statické a dynamické knihovny při použití [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) možnost. Například této chybě může dojít, pokud vytváření knihovny DLL pro použití v vaší spustitelný soubor odkazující v statické CRT. Chcete-li tento problém vyřešit, použijte pouze statické knihovny nebo jenom dynamické knihovny pro celý spustitelný soubor a pro všechny knihovny, které vytvoříte pro použití v spustitelný soubor.  
  
-   Této chybě může dojít, pokud symbol je zabalené funkce (vytvořený kompilací s [/Gy](../../build/reference/gy-enable-function-level-linking.md)) a je zahrnutý ve víc než jeden soubor, ale byl změněn mezi kompilace. Chcete-li tento problém vyřešit, znovu zkompiluje všechny soubory, které zahrnují zabalené funkce.  
  
-   Této chybě může dojít, pokud symbol je definována jinak v dva objekty člen v různé knihovny, a obě člen objekty se používají. Jeden způsob, jak tento problém vyřešit, když jsou staticky propojené knihovny je použít objekt člena z jenom jeden knihovny, a musí zahrnovat této knihovny nejdřív na příkazový řádek linkeru. Pokud chcete používat obě symboly, je nutné vytvořit způsob, jak je odlišili. Například můžete vytvořit knihovny ze zdroje, může obtékat jednotlivých knihoven v jedinečný obor názvů. Alternativně můžete vytvořit novou obálku knihovnu, která používá jedinečné názvy zabalení odkazy na jednu z původní knihovny, propojit původní knihovna nové knihovny a pak propojte spustitelný soubor do nové knihovny místo původní knihovna.  
  
-   Této chybě může dojít, pokud `extern const` proměnné je definován dvakrát a má v každé definici jinou hodnotu. Chcete-li tento problém vyřešit, definovat konstantní jen jednou nebo použijte obory názvů nebo `enum class` definice k rozlišení konstanty.  
  
-   Této chybě může dojít, pokud používáte uuid.lib v kombinaci s ostatními soubory .lib, které definují identifikátory GUID (například oledb.lib a adsiid.lib). Příklad:  
  
    ```Output  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     Chcete-li tento problém vyřešit, přidejte [/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) možnosti příkazového řádku linkeru a ujistěte se, že tento uuid.lib je první knihovny odkazuje.
  
## <a name="additional-information"></a>Další informace  
  
Pokud používáte starší verzi sady nástrojů, naleznete v článcích znalostní báze Knowledge Base další informace o konkrétní příčiny této chyby:  
  
-   [LNK2005 chyba nastane, když jsou v nesprávném pořadí v jazyce Visual C++ propojené knihovny CRT a knihovny MFC](https://support.microsoft.com/kb/148652)  
  
-   [Oprava: Globální přetížené odstranit operátor příčiny LNK2005](https://support.microsoft.com/kb/140440)  
  
-   [Při kompilaci projektu knihovny ATL spustitelný soubor (.exe) v jazyce Visual C++, zobrazí se chyba LNK2005](https://support.microsoft.com/kb/184235).  
  
