---
title: Windows Sockets – třídy
ms.date: 11/04/2016
f1_keywords:
- vc.classes.net
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 18537c0de09185c8cd219e3d17ef8bb297e1d711
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433602"
---
# <a name="windows-sockets-classes"></a>Windows Sockets – třídy

Windows Sockets poskytují způsob protokol nezávislé sítě ke komunikaci mezi dvěma počítači. Může být synchronní tyto sokety (program čeká, dokud probíhá komunikace), nebo asynchronní (váš program bude pokračovat při komunikaci se děje).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Zapouzdřuje rozhraní Windows Sockets API v obálce dynamického zajišťování.

[Csocket –](../mfc/reference/csocket-class.md)<br/>
Vyšší úrovni abstrakce odvozený od `CAsyncSocket`. Pracuje synchronně.

[Csocketfile –](../mfc/reference/csocketfile-class.md)<br/>
Poskytuje `CFile` rozhraní Windows Socket.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

