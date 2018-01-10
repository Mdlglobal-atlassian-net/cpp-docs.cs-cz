---
title: "Definice funkcí jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function declarators
- function definitions
- declaring functions, about function declarations
- declaring functions, declarators
- functions [C], parameters
- declarators, functions
- function parameters, function definitions
- function body
- declaring functions, variables
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a58adfefc5e2b3b5085a44c38dd392d3369421c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c-function-definitions"></a>Definice funkcí jazyka C
Definice funkce určuje název funkce, typy a počet parametrů, které lze přijímat a její návratový typ. Definice funkce také obsahuje tělo funkce s deklarací o jeho místní proměnné a příkazy, které určují, jaké funkce.  
  
## <a name="syntax"></a>Syntaxe  
 *jednotky překladu*:  
 *externí deklarace*  
  
 *jednotky překladu externí – deklarace*  
  
 *externí deklarace*: /\* povoleny pouze v oboru externí (soubor)\*/  
 *definice funkce*  
  
 `declaration`  
  
 *definice funkce*: /\* deklarátor tady je deklarátor – funkce\*/  
 *specifikátory deklarace* vyjádřit výslovný*atribut seq* opt*deklarátor deklarace list* opt*složené – příkaz*  
  
 /\**atribut seq* je specifické pro Microsoft * /  
  
 Prototyp parametry jsou:  
  
 *specifikátory deklarace*:  
 *specifikátor třídy úložiště specifikátory deklarace* opt  
  
 *Specifikátor typu deklarace – specifikátory* opt  
  
 *Kvalifikátor typu deklarace – specifikátory* opt  
  
 *seznam prohlášení*:  
 *deklarace*  
  
 *seznam prohlášení deklarace*  
  
 `declarator`:  
 *ukazatel* opt*přímo deklarátor*  
  
 *deklarátor přímo*: /\* deklarátor – funkce\*/  
 *deklarátor přímo***(***seznam parametrů typu***)** / * deklarátor nový styl      \*/  
  
 *deklarátor přímo***(***seznam identifikátorů* opt**)** / * deklarátor zastaralé stylu    \*/  
  
 Seznam parametrů v definici používá tuto syntaxi:  
  
 *Seznam parametrů typu*: /\* seznam parametrů\*/  
 *Seznam parametrů*  
  
 *Seznam parametrů* **,...**  
  
 *Seznam parametrů*:  
 *deklarace parametru*  
  
 *Seznam parametrů* **,***deklarace parametru*   
  
 *deklarace parametru*:  
 *deklarátor specifikátory deklarace*  
  
 *specifikátory deklarace abstraktní deklarátor* opt  
  
 Seznam parametrů v definici funkce starého používá tuto syntaxi:  
  
 *Seznam identifikátorů*: /\* používán funkce zastaralé stylu definice a deklarace\*/  
 *identifikátor*  
  
 *Seznam identifikátorů* **,***identifikátor*   
  
 Tady je syntax pro tělo funkce:  
  
 *příkaz složené*: /\* tělo funkce\*/  
 **{**`declaration`-*seznamu* opt*seznam příkazů* opt**}**   
  
 Jsou pouze specifikátory třídy úložiště, které můžete upravit deklaraci funkce `extern` a **statické**. `extern` Specifikátor označuje, že funkce lze odkazovat z jiných souborů; to znamená, že je název funkce exportován do linkeru. **Statické** specifikátor označuje, že funkci nelze na něj odkazovat z jiných souborů; to znamená, není název exportované sadou linkeru. Pokud neexistuje žádná třída úložiště se zobrazí v definici funkce `extern` se předpokládá. Funkce je v každém případě vždy viditelné z definice bodu na konec souboru.  
  
 Volitelné *specifikátory deklarace* a povinné `declarator` společně zadat návratový typ funkce a název. `declarator` Je kombinací identifikátor, který názvy funkce a závorek název funkce. Volitelné *atribut seq* nonterminal je Microsoft specifické funkce, které jsou definované v [atributy funkce](../c-language/function-attributes.md).  
  
 *Přímo deklarátor* (v `declarator` syntaxe) určuje název funkce definovaný a identifikátory její parametry. Pokud *přímo deklarátor* zahrnuje *seznam parametrů typu*, seznamu určuje typy všechny parametry. Takové deklarátor slouží také jako prototyp funkce pro pozdější volání funkce.  
  
 A `declaration` v *seznam prohlášení* ve funkci nesmí obsahovat definice *specifikátor třídy úložiště* jiné než **zaregistrovat**. *Specifikátor typu* v *specifikátory deklarace* pouze, pokud lze vynechat syntaxe **zaregistrovat** třídy úložiště je zadán pro hodnotu `int` typu.  
  
 *Složené příkaz* tělo funkce obsahující místní deklarace proměnných a odkazy na deklarované externě položky a příkazy.  
  
 V částech [atributy funkce](../c-language/function-attributes.md), [třídy úložiště](../c-language/storage-class.md), [návratového typu](../c-language/return-type.md), [parametry](../c-language/parameters.md), a [tělo funkce](../c-language/function-body.md) součástí definice funkce podrobně popisují.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../c-language/functions-c.md)