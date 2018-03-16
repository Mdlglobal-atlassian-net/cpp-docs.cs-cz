---
title: Parametry | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipses (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e73e7aa3ff62782c6ebd3b5a8728aa05e78b1784
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="parameters"></a>Parametry
Argumenty jsou názvy hodnot předaná funkci volání funkce. Parametry jsou hodnoty, které funkce očekává přijímat. Prototyp funkce závorek název funkce obsahovat úplný seznam parametrů funkce a jejich typy. Deklarace parametru zadejte typy, velikosti a identifikátory hodnot uložených v parametrech.  
  
## <a name="syntax"></a>Syntaxe  
 *definice funkce*:  
 *specifikátory deklarace* vyjádřit výslovný*atribut seq* opt*deklarátor deklarace list* opt*složené – příkaz*  
  
 /\* *atribut seq* je specifické pro Microsoft * /  
  
 *deklarátor* :  
 *ukazatel* opt*přímo deklarátor*  
  
 *deklarátor přímo*:/\* deklarátor – funkce \*/  
 *deklarátor přímo***(***seznam parametrů typu***)** / * deklarátor nový styl       \*/  
  
 *Seznam parametrů typu*: /\* seznam parametrů \*/  
 *parameter-list*  
  
 *Seznam parametrů***,...**   
  
 *parameter-list*:  
 *parameter-declaration*  
  
 *Seznam parametrů***,***deklarace parametru*   
  
 *parameter-declaration*:  
 *deklarátor specifikátory deklarace*  
  
 *specifikátory deklarace abstraktní – deklarátor* opt  
  
 *Seznam parametrů typu* je posloupnost deklarace parametrů oddělených čárkami. Formuláře v seznamu parametrů. každý parametr vypadá takto:  
  
```  
[register]  type-specifier [declarator]   
```  
  
 Parametry funkce deklarovat s **automaticky** atribut generují chyby. Identifikátory parametry se používají v těle funkce odkazovat na hodnoty předaný funkci. Můžete pojmenovat parametrů v prototyp, ale názvy se dostala mimo rozsah na konci tohoto prohlášení. Proto názvy parametrů lze přiřadit stejný způsobem nebo jinak v definici funkce. Tyto identifikátory nelze jej předefinovat v nejkrajnější blok tělo funkce, ale jejich můžete jej předefinovat v informacích o vnitřní, vnořené bloky, jako by byl vnějšího bloku seznam parametrů.  
  
 Každý identifikátor v *seznam parametrů typu* musí předcházet jeho příslušného typu specifikátor, jak je uvedeno v následujícím příkladu:  
  
```  
void new( double x, double y, double z )  
{  
    /* Function body here */  
}  
```  
  
 V případě minimálně jeden parametr v seznamu parametrů seznamu můžete ukončit středníkem, za nímž následuje tři tečky (**,...** ). Tato konstrukce, nazývá "třemi tečkami notace," označuje proměnný počet argumentů funkce. (Viz [volání proměnné počet argumentů](../c-language/calls-with-a-variable-number-of-arguments.md) Další informace.) Volání funkce však musí obsahovat alespoň tolik argumenty, jako jsou parametry před poslední čárkou.  
  
 Pokud žádné argumenty předávané funkce, seznam parametrů je nahrazena klíčové slovo `void`. Toto použití `void` se liší od jeho použití jako specifikátor typu.  
  
 Pořadí a typ parametry, včetně žádné použití notace třemi tečkami, musí být stejná ve všech deklarace funkce (pokud existuje) a v definici funkce. Typy argumentů po obvyklé aritmetické převody musí být přiřazení kompatibilní s typy odpovídajících parametrů. (Viz [obvyklé aritmetické převody](../c-language/usual-arithmetic-conversions.md) informace o aritmetické převody.) Následující se třemi tečkami argumenty nejsou zaškrtnutí. Parametr můžete mít všechny základní struktury, sjednocení, ukazatele, nebo typ pole.  
  
 Kompilátor obvyklé aritmetické převody nezávisle na každý parametr a na každý argument, v případě potřeby provede. Po převodu, je kratší než žádný parametr `int`, a nemá žádný parametr **float** zadejte výslovně uvedeno s typem parametru jako **float** v prototypu. To znamená, například deklarace jako parametr `char` má stejně, jako je jako deklarace `int`.  
  
## <a name="see-also"></a>Viz také  
 [Definice funkcí jazyka C](../c-language/c-function-definitions.md)