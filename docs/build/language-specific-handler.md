---
title: Obslužná rutina specifická pro jazyk | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6503e0cd-2d3a-4330-a925-8bed8c27c2be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 678f5695523751ebc1ef3c5dba2b63154b21833c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714945"
---
# <a name="language-specific-handler"></a>Obslužná rutina specifická pro jazyk

Pokaždé, když jsou nastaveny příznaky UNW_FLAG_EHANDLER nebo UNW_FLAG_UHANDLER se nachází v UNWIND_INFO relativní adresu obslužná rutina pro konkrétní jazyk. Jak je popsáno v předchozí části, je volána obslužná rutina pro konkrétní jazyk jako součást hledání pro obslužnou rutinu výjimky, nebo jako součást unwind. Má následující prototyp:

```
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** poskytuje ukazatel na záznam o výjimce, která má standardní definice Win64.

**EstablisherFrame** je adresa base pevné přidělení zásobníku pro tuto funkci.

**ContextRecord** body ke kontextu výjimky v době byla vyvolána výjimka (v případě obslužné rutiny výjimek) nebo aktuální kontext (v případě obslužné rutiny ukončení) "unwind".

**DispatcherContext** odkazuje na dispečer kontext pro tuto funkci. Má následující definice:

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

**ControlPc** je hodnota RIP v rámci této funkce. Toto je adresa výjimky nebo adresu, ve kterém ovládací prvek vlevo o funkce. Toto je RIP, který se použije k určení, zda je ovládací prvek v rámci některé chráněné konstrukce v rámci této funkce (například, blok __try pro \__try /\__except nebo \__try /\__finally).

**Hodnotu ImageBase** je obrázek základní (zatížení adresa) modul obsahující tuto funkci, a přidat do 32-bit odsazení použité v položce funkce unwind info k zaznamenání relativní adresy.

**FunctionEntry** poskytuje ukazatel RUNTIME_FUNCTION funkce položka uchovávající funkce a unwind info relativní adresy základní image pro tuto funkci.

**EstablisherFrame** je adresa base pevné přidělení zásobníku pro tuto funkci.

**TargetIp** poskytuje adresu volitelné instrukce, která určuje adresu pokračování procesu odvíjení. Tato adresa se ignoruje, pokud **EstablisherFrame** není zadán.

**ContextRecord** odkazuje na kontext výjimky pro použití kódem odeslání/unwind výjimek systému.

**LanguageHandler** odkazuje na konkrétní jazyk obslužné rutině, volána.

**HandlerData** odkazuje na obslužné rutiny specifické pro jazyk data pro tuto funkci.

## <a name="see-also"></a>Viz také

[Zpracování výjimek (x64)](../build/exception-handling-x64.md)