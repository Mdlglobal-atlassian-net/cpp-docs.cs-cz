---
title: Třídy úložiště | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecd50ddf72fbafb23571e2b2709418e4eb89093e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="storage-class"></a>Třída úložiště
Specifikátor třídy úložiště v definici funkce nabízí funkce buď `extern` nebo **statické** třídy úložiště.  
  
## <a name="syntax"></a>Syntaxe  
 *definice funkce*:  
 *specifikátory deklarace* vyjádřit výslovný*atribut seq* opt*deklarátor deklarace list* opt*složené – příkaz*  
  
 /\* *atribut seq* je specifické pro Microsoft * /  
  
 *specifikátory deklarace*:  
 *specifikátor třídy úložiště specifikátory deklarace* opt  
  
 *Specifikátor typu deklarace – specifikátory* opt  
  
 *Kvalifikátor typu deklarace – specifikátory* opt  
  
 *specifikátor třídy úložiště*: /\* pro definice funkcí \*/  
 **extern**  
  
 **static**  
  
 Pokud neobsahuje definici funkce *specifikátor třídy úložiště*, použije se výchozí hodnota třídy úložiště `extern`. Funkci lze explicitně deklarovat jako `extern`, není to však zapotřebí.  
  
 Pokud obsahuje deklaraci funkce *specifikátor třídy úložiště* `extern`, identifikátor má stejné propojení jako žádné viditelné deklarace identifikátoru s rozsahem souboru. Pokud v oboru souboru neexistuje žádná viditelná deklarace, má identifikátor vnější propojení. Pokud má identifikátor rozsah souboru a ne *specifikátor třídy úložiště*, externí propojení nemá identifikátor. Vnější propojení znamená, že všechny instance identifikátoru označují stejný objekt nebo funkci. V tématu [doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md) Další informace o propojení a soubor oboru.  
  
 Deklarace funkcí v oboru bloku se specifikátorem třídy úložiště jiným než `extern` generují chyby.  
  
 Funkce s **statické** třídy úložiště je viditelná pouze v zdrojový soubor, ve kterém je definovaný. Všechny ostatní funkce s třídou úložiště `extern` zadanou explicitně či implicitně jsou viditelné ve všech zdrojových souborech programu. Pokud **statické** třídy úložiště se požaduje, se musí být deklarován v prvním výskytem deklarace (pokud existuje), funkce a v definici funkce.  
  
 **Konkrétní Microsoft**  
  
 Pokud jsou povolené rozšíření Microsoft, funkce původně deklarovány bez třídy úložiště (nebo s `extern` třídy úložiště) je zadána **statické** úložiště třídy, pokud definice této funkce je ve stejném souboru zdroje a pokud definice explicitně určuje **statické** třídy úložiště.  
  
 Je-li program kompilován s možností kompilátoru /Ze, funkce deklarované uvnitř bloku pomocí klíčového slova `extern` mají globální viditelnost. To neplatí v případě kompilace s možností /Za. Tato funkce nemusí být spolehlivá, bere-li se v úvahu přenositelnost zdrojového kódu.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Definice funkcí jazyka C](../c-language/c-function-definitions.md)