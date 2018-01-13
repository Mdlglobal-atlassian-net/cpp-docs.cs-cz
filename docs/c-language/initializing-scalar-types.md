---
title: "Inicializace skalárních typů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- initializing scalar types
- register variables
- initialization, scalar types
- initializing variables, scalar types
- scalar types
- static variables, initializing
- automatic storage class, initializing scalar types
- automatic storage class
- types [C], initializing
ms.assetid: 73c516f5-c3ad-4d56-ab3b-f2a82b621104
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e3863ea5a6edfd0c7bc605231182a8d5dfc17b9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="initializing-scalar-types"></a>Inicializace skalárních typů
Při inicializaci Skalární typy, hodnota *přiřazení výraz* je přiřazen k proměnné. Pravidla převodu pro přiřazení platit. (Viz [převody typů](../c-language/type-conversions-c.md) informace o pravidel převodu.)  
  
## <a name="syntax"></a>Syntaxe  
 `declaration`:  
 *specifikátory deklarace init deklarátor list* opt**;**  
  
 *specifikátory deklarace*:  
 *specifikátor třídy úložiště specifikátory deklarace* opt  
  
 *Specifikátor typu deklarace – specifikátory* opt  
  
 *Kvalifikátor typu deklarace – specifikátory* opt  
  
 *Init – deklarátor seznamu*:  
 *Init – deklarátor*  
  
 *Init – deklarátor seznamu***,***init deklarátor*   
  
 *Init – deklarátor*:  
 *deklarátor*  
  
 *deklarátor***=***inicializátoru* / * pro skalární inicializace    \*/  
  
 *Inicializátor*:  
 *přiřazení – výraz*  
  
 Proměnné libovolného typu, můžete inicializovat za předpokladu, že vyhovují následujícím pravidlům:  
  
-   Proměnných deklarovaných na úrovni oboru soubor může být inicializována. Pokud proměnnou na externí úrovni není explicitně inicializovat, je inicializováno 0 ve výchozím nastavení.  
  
-   Konstantní výraz slouží k inicializaci všechny globální proměnná deklarovat s **statické** *specifikátor třídy úložiště*. Proměnné deklarovány jako **statické** jsou inicializovány při zahájení spuštění programu. Pokud není inicializaci explicitně globální konfiguraci **statické** proměnné, je inicializováno 0 ve výchozím nastavení, a každý člen, který má ukazatel typu přiřazený ukazatele null.  
  
-   Proměnné deklarovat s **automaticky** nebo **zaregistrovat** – specifikátor třídy úložiště jsou inicializovány při každém spuštění ovládací prvek předává do bloku ve které jsou deklarované. Pokud vynecháte inicializátoru z deklaraci **automaticky** nebo **zaregistrovat** proměnné, počáteční hodnota proměnné není definován. Pro automatické a hodnot registru, inicializátoru není omezen na právě konstanta; může být jakýkoli výraz zahrnující dříve definované hodnoty, i funkce volání.  
  
-   Počáteční hodnoty pro externí deklarace proměnných a pro všechny **statické** proměnné, zda vnější nebo vnitřní, musí být konstantní výrazy. (Další informace najdete v tématu [konstantní výrazy](../c-language/c-constant-expressions.md).) Protože adresu žádné externě deklarované nebo statické proměnné je konstanta, může sloužit k chybě při inicializaci interně deklarované **statické** proměnné ukazatele. Ale adresu **automaticky** proměnné nelze použít jako inicializátoru statické, protože může být různé pro každé spuštění bloku. Konstantní nebo proměnných hodnot můžete použít k chybě při inicializaci **automaticky** a **zaregistrovat** proměnné.  
  
-   Pokud deklarace identifikátoru obsahuje rozsah bloku a identifikátor má externí propojení, nemůže mít deklaraci inicializaci.  
  
## <a name="examples"></a>Příklady  
 Následující příklady ilustrují inicializacích:  
  
```  
int x = 10;   
```  
  
 Proměnná s celým číslem `x` je inicializováno konstantní výraz `10`.  
  
```  
register int *px = 0;  
```  
  
 Ukazatele `px` je inicializován na 0, který vytvořil ukazatele "null".  
  
```  
const int c = (3 * 1024);  
```  
  
 Tento příklad používá konstantní výraz `(3 * 1024)` k chybě při inicializaci `c` na konstantní hodnotu, která nemůže být upravena z důvodu **const** – klíčové slovo.  
  
```  
int *b = &x;  
```  
  
 Tento příkaz inicializuje ukazatele `b` s adresou jiné proměnné `x`.  
  
```  
int *const a = &z;  
```  
  
 Ukazatele `a` inicializován s adresu proměnné s názvem `z`. Ale protože je zadán jako **const**, proměnná `a` lze inicializovat pouze, nikdy změnit. Vždycky směřuje na stejné umístění.  
  
```  
int GLOBAL ;  
  
int function( void )  
{  
    int LOCAL ;  
    static int *lp = &LOCAL;   /* Illegal initialization */  
    static int *gp = &GLOBAL;  /* Legal initialization   */  
    register int *rp = &LOCAL; /* Legal initialization   */  
}  
```  
  
 Globální proměnné `GLOBAL` je deklarovaná na externí úrovni, má globální doba platnosti. Místní proměnná `LOCAL` má **automaticky** třídy úložiště a má jenom adresu během provádění funkce, ve kterém je deklarovaná. Proto Probíhá pokus o inicializaci **statické** proměnné ukazatele `lp` s adresou `LOCAL` není povoleno. **Statické** proměnné ukazatele `gp` jde inicializovat na adresu `GLOBAL` vzhledem k tomu, že adresa je vždy stejný. Podobně `*rp` můžete inicializovat, protože `rp` je místní proměnné a může mít inicializátoru nonconstant. Pokaždé, když je zadaný blok, `LOCAL` má novou adresu, která je pak přiřazená `rp`.  
  
## <a name="see-also"></a>Viz také  
 [Inicializace](../c-language/initialization.md)