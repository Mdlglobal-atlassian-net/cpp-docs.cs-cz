---
title: Multithreading s použitím jazyka C a Win32 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09397b5a60dcc2cbe2b3e6265f6080f3c5c1e212
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428093"
---
# <a name="multithreading-with-c-and-win32"></a>Multithreading s použitím jazyka C a prostředí Win32

Microsoft Visual C++ poskytuje podporu pro vytváření aplikací s více vlákny. Měli byste zvážit použití více než jedno vlákno, pokud vaše aplikace potřebuje provádět nákladné operace, které by mohly způsobit uživatelského rozhraní přestane reagovat.

V jazyce Visual C++ existují dva způsoby programování s více vlákny: pomocí knihovny Microsoft Foundation Class (MFC) nebo knihovny run-time jazyka C a rozhraní API systému Win32. Informace o vytváření aplikací s více vlákny s knihovnou MFC naleznete v tématu [Multithreading s C++ a knihovnou MFC](multithreading-with-cpp-and-mfc.md) po přečtení následujících témat o multithreading v C.

Tato témata vysvětlují funkce v jazyce Visual C++ pro podporu vytváření programů s více vlákny.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Co multithreading spočívá v](multithread-programs.md)

- [Podpora knihovny pro multithreading](library-support-for-multithreading.md)

- [Zahrnuté soubory pro multithreading](include-files-for-multithreading.md)

- [Funkce knihovny C Run-Time pro řízení vláken](c-run-time-library-functions-for-thread-control.md)

- [Ukázka vícevláknového programu v jazyce C](sample-multithread-c-program.md)

- [Psaní programů s více vlákny pro Win32](writing-a-multithreaded-win32-program.md)

- [Kompilování a propojování programů s více vlákny](compiling-and-linking-multithread-programs.md)

- [Obcházení problémových oblastí pomocí programů s více vlákny](avoiding-problem-areas-with-multithread-programs.md)

- [Úložiště thread local (TLS)](thread-local-storage-tls.md)

## <a name="see-also"></a>Viz také

[Podpora multithreadingu ve starším kódu (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)