---
title: Windows Sockets – třídy
ms.date: 11/04/2016
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 3f1b7b2b6674b4a5f8c8f7bff6c5fa239715f459
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445983"
---
# <a name="windows-sockets-classes"></a>Windows Sockets – třídy

Windows Sockets poskytuje způsob, jak komunikovat mezi dvěma počítači, nezávisle na síťovém protokolu. Tyto sokety můžou být synchronní (váš program čeká na dokončení komunikace) nebo asynchronní (program pokračuje v běhu, i když probíhá komunikace).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Zapouzdřuje rozhraní Windows Sockets API v tenké obálce.

[CSocket –](../mfc/reference/csocket-class.md)<br/>
Abstrakce vyšší úrovně odvozená od `CAsyncSocket`. Funguje synchronně.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Poskytuje `CFile` rozhraní k soketu Windows.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
