---
title: extern – specifikátor třídy úložiště | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08a578514aaf6de4132bd856900b0ec31d31835c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388725"
---
# <a name="extern-storage-class-specifier"></a>extern – specifikátor třídy úložiště
Proměnná deklarovaná pomocí specifikátoru paměťové třídy `extern` je odkaz na proměnnou se stejným názvem, která je definovaná na vnější úrovni v jakémkoli zdrojovém souboru programu. Pomocí vnitřní deklarace `extern` lze definice proměnné na vnější úrovni zviditelnit v rámci bloku. Není-li na vnější úrovni deklarováno jinak, je proměnná deklarovaná pomocí klíčového slova `extern` viditelná pouze v bloku, ve kterém je deklarována.  
  
## <a name="example"></a>Příklad  
 Tento příklad ilustruje deklarace na vnitřní a vnější úrovni:  
  
```  
// extern_StorageClassSpecified.c  
#include <stdio.h>  
  
void other( void );  
  
int main()  
{  
    // Reference to i, defined below:   
    extern int i;  
  
    // Initial value is zero; a is visible only within main:   
    static int a;  
  
    // b is stored in a register, if possible:   
    register int b = 0;  
  
    // Default storage class is auto:   
    int c = 0;  
  
    // Values printed are 1, 0, 0, 0:   
    printf_s( "%d\n%d\n%d\n%d\n", i, a, b, c );  
    other();  
    return;  
}  
  
int i = 1;  
  
void other( void )  
{  
    // Address of global i assigned to pointer variable:  
    static int *external_i = &i;  
  
    // i is redefined; global i no longer visible:   
    int i = 16;  
  
    // This a is visible only within the other function:   
    static int a = 2;  
  
    a += 2;  
    // Values printed are 16, 4, and 1:  
    printf_s( "%d\n%d\n%d\n", i, a, *external_i );  
}  
```  
  
 V tomto příkladu je proměnná `i` definována na vnější úrovni s počáteční hodnotou 1. Deklarace `extern` ve funkci `main` umožňuje deklarovat odkaz na proměnnou `i` na vnější úrovni. **Statické** proměnná `a` je inicializováno 0 ve výchozím nastavení, protože inicializátoru je vynechán. Volání funkce `printf` vypíše hodnoty 1, 0, 0 a 0.  
  
 V `other` funkce, adresa globální proměnná `i` slouží k inicializaci **statické** proměnné ukazatele `external_i`. Toto funguje, protože má globální proměnná **statické** životnost, což znamená jeho adresy nezmění při spuštění programu. Dále je proměnná `i` redefinována jako místní proměnná s počáteční hodnotou 16. Tato redefinice nemá vliv na hodnotu proměnné `i` na externí úrovni, která je pomocí jejího názvu jako lokální proměnné skryta. Hodnota globální proměnné `i` je nyní v rámci tohoto bloku přístupná pouze nepřímo pomocí ukazatele `external_i`. Probíhá pokus o přiřazení na adresu **automaticky** proměnná `i` na ukazatel nefunguje, protože může být jiné pokaždé, když se zadá bloku. Proměnná `a` je deklarován jako **statické** proměnné a inicializovaný 2. To `a` není v konfliktu s `a` v `main`, od **statické** proměnné na interní úrovni jsou viditelné pouze v rámci bloku ve které jsou deklarované.  
  
 Proměnná `a` je zvýšena o 2 a výsledek je 4. Pokud by byla funkce `other` volána znovu ve stejném programu, počáteční hodnota proměnné `a` by byla 4. Interní **statické** proměnné zachovat jejich hodnoty, když se program ukončí a pak reenters bloku ve které jsou deklarované.  
  
## <a name="see-also"></a>Viz také  
 [Specifikátory třídy úložiště pro deklarace na interní úrovni](../c-language/storage-class-specifiers-for-internal-level-declarations.md)