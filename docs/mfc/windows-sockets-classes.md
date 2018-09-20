---
title: Windows Sockets – třídy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.net
dev_langs:
- C++
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 893fa525b04376cde0e96f280c95e6bfd1243946
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439975"
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

