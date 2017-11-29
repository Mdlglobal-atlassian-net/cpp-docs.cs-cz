---
title: "Odkaz Možnosti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- nothrownew.obj
- newmode.obj
- noenv.obj
- psetargv.obj
- loosefpmath.obj
- smallheap.obj
- fp10.obj
- nochkclr.obj
- chkstk.obj
- pcommode.obj
- pnoenv.obj
- link options [C++]
- invalidcontinue.obj
- pnothrownew.obj
- pwsetargv.obj
- pinvalidcontinue.obj
- wsetargv.obj
- binmode.obj
- setargv.obj
- noarg.obj
- pnewmode.obj
- commode.obj
- pthreadlocale.obj
- pbinmode.obj
- threadlocale.obj
- pnoarg.obj
ms.assetid: 05b5a77b-9dd1-494b-ae46-314598c770bb
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7e22f2d3c69bf4f0daf38c4f59b416d8d44a431a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="link-options"></a>Možnosti odkazů
Adresáři lib CRT zahrnuje několik malých objekt soubory, které povolit konkrétní funkce CRT bez jakékoli změny kódu. Toto nastavení se nazývá "odkaz Možnosti" vzhledem k tomu, že máte právě je přidáte do příkazového řádku linkeru jejich použití.  
  
 Čistý režimu verze existují, ale jsou zastaralé v sadě Visual Studio 2015. Používat regulární verze pro nativní a možnost/CLR kód, použijte čisté verze (s předponou p) pro/CLR: pure režimu. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
|Nativní a možnost/CLR|Čistý režimu|Popis|  
|----------------------|---------------|-----------------|  
|binmode.obj|pbinmode.obj|Nastaví výchozí režim překladu souborů na binární soubor. V tématu [_fmode –](../c-runtime-library/fmode.md).|  
|chkstk.obj|není k dispozici|Poskytuje podporu kontrolu zásobníku a alloca – Pokud nepoužíváte CRT.|  
|commode.obj|pcommode.obj|Nastaví příznak globálního potvrzení "potvrzení". V tématu [fopen –, _wfopen –](../c-runtime-library/reference/fopen-wfopen.md) a [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md).|  
|fp10.obj|není k dispozici|Změny ovládacího prvku výchozí přesnost 64 bitů. V tématu [podpora plovoucí desetinné čárky](../c-runtime-library/floating-point-support.md).|  
|invalidcontinue.obj|pinvalidcontinue.obj|Nastaví výchozí obslužnou rutinu neplatný parametr, který nic neprovádí, což znamená, že neplatné parametry předaný funkcí CRT se právě nastavit kód chyby a vrátí výsledek chyby.|  
|loosefpmath.obj|není k dispozici|Zajišťuje, že plovoucí kód bodu toleruje denormal hodnoty.|  
|newmode.obj|pnewmode.obj|Způsobí, že [malloc](../c-runtime-library/reference/malloc.md) volat novou obslužnou rutinu při selhání. V tématu [_set_new_mode –](../c-runtime-library/reference/set-new-mode.md), [_set_new_handler –](../c-runtime-library/reference/set-new-handler.md), [calloc –](../c-runtime-library/reference/calloc.md), a [realloc –](../c-runtime-library/reference/realloc.md).|  
|noarg.obj|pnoarg.obj|Veškeré zpracování argc – a argv – zakáže.|  
|nochkclr.obj|není k dispozici|Neprovádí žádnou akci. Odeberte ze svého projektu.|  
|noenv.obj|pnoenv.obj|Vytvoření prostředí v mezipaměti pro CRT zakáže.|  
|nothrownew.obj|pnothrownew.obj|Umožňuje – vyvolání verze nové v CRT. V tématu [nové a odstraňte operátory](../cpp/new-and-delete-operators.md).|  
|setargv.obj|psetargv.obj|Umožňuje rozšíření zástupného znaku argument příkazového řádku. V tématu [rozšíření argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).|  
|threadlocale.obj|pthreadlocale.obj|Umožňuje vlákno národní prostředí pro všechny nové vláken ve výchozím nastavení.|  
|wsetargv.obj|pwsetargv.obj|Umožňuje rozšíření zástupného znaku argument příkazového řádku. V tématu [rozšíření argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).|  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)