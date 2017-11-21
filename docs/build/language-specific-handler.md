---
title: "Obslužná rutina specifická pro jazyk | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6503e0cd-2d3a-4330-a925-8bed8c27c2be
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3f9e548dc3c9262349fc05bd6bea19290b57ad94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="language-specific-handler"></a>Obslužná rutina specifická pro jazyk
Vždy, když jsou nastaveny příznaky UNW_FLAG_EHANDLER nebo UNW_FLAG_UHANDLER se nachází v UNWIND_INFO relativní adresu obslužná rutina pro konkrétní jazyk. Jak je popsáno v předchozí části, se nazývají obslužná rutina pro konkrétní jazyk, v rámci hledání pro obslužnou rutinu výjimky nebo jako součást unwind. Má následující prototyp:  
  
```  
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (  
    IN PEXCEPTION_RECORD ExceptionRecord,  
    IN ULONG64 EstablisherFrame,  
    IN OUT PCONTEXT ContextRecord,  
    IN OUT PDISPATCHER_CONTEXT DispatcherContext  
);  
```  
  
 **ExceptionRecord** dodává ukazatel na záznam výjimky, který má standardní definici Win64.  
  
 **EstablisherFrame** je adresa základu pevné přidělení zásobníku pro tuto funkci.  
  
 **ContextRecord** body na kontext výjimky v době byla vyvolána výjimka (v případě obslužné rutiny výjimky) nebo aktuální kontext (v případě obslužné rutiny ukončení) "unwind".  
  
 **DispatcherContext** odkazuje na kontext dispečera pro tuto funkci. Obsahuje následující definice:  
  
```  
typedef struct _DISPATCHER_CONTEXT {  
    ULONG64 ControlPc;  
    ULONG64 ImageBase;  
    PRUNTIME_FUNCTION FunctionEntry;  
    ULONG64 EstablisherFrame;  
    ULONG64 TargetIp;  
    PCONTEXT ContextRecord;  
    PEXCEPTION_ROUTINE LanguageHandler;  
    PVOID HandlerData;  
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;  
```  
  
 **ControlPc** je hodnota RIP v rámci této funkce. Toto je adresa výjimky nebo adresu, na které prvek levé sestavovací funkci. Toto je RIP, který se použije k určení, pokud je v rámci některé chráněné konstrukce v rámci této funkce řízení (například blok __try pro \__try /\__except nebo \__try /\__finally).  
  
 **ImageBase** je image základní (zatížení adresu) modul, který obsahuje tato funkce a přidat do 32-bit posunutí použít ve vstupu unwind info a na zaznamenání adres.  
  
 **FunctionEntry** zdroje a odkazy RUNTIME_FUNCTION funkce položku, která uchovává funkce a unwind info základní bitovou kopii pro tuto funkci.  
  
 **EstablisherFrame** je adresa základu pevné přidělení zásobníku pro tuto funkci.  
  
 **TargetIp** poskytuje volitelné instrukce adresu, která určuje adresu pokračování unwind. Tato adresa je ignorována, pokud **EstablisherFrame** není zadán.  
  
 **ContextRecord** odkazuje na kontext výjimky pro použití v odesílání/unwind kód výjimky systému.  
  
 **LanguageHandler** odkazuje na obslužnou rutinu konkrétní jazyk volána.  
  
 **HandlerData** odkazuje na obslužnou rutinu pro specifický jazyk data pro tuto funkci.  
  
## <a name="see-also"></a>Viz také  
 [(X64) zpracování výjimek](../build/exception-handling-x64.md)