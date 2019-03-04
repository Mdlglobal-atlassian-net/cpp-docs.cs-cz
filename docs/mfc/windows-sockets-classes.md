---
title: Windows Sockets – třídy
ms.date: 11/04/2016
f1_keywords:
- vc.classes.net
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 4abdd8f8fbfc115b5014ffd0b3a37df357852b16
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303817"
---
# <a name="windows-sockets-classes"></a>Windows Sockets – třídy

Windows Sockets poskytují způsob protokol nezávislé sítě ke komunikaci mezi dvěma počítači. Může být synchronní tyto sokety (program čeká, dokud probíhá komunikace), nebo asynchronní (váš program bude pokračovat při komunikaci se děje).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Zapouzdřuje rozhraní Windows Sockets API v obálce dynamického zajišťování.

[CSocket](../mfc/reference/csocket-class.md)<br/>
Vyšší úrovni abstrakce odvozený od `CAsyncSocket`. Pracuje synchronně.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Poskytuje `CFile` rozhraní Windows Socket.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
