---
title: 'Windows Sockets: Převádění řetězců | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b23d2149659cdad320a58bdff0f42ba113b5696
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378933"
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets: Převádění řetězců

V tomto článku a dva doprovodné články popisují několik problémů v programování v rozhraní Windows Sockets. Tento článek se týká převádění řetězců. Další problémy se věnují [rozhraní Windows Sockets: blokování](../mfc/windows-sockets-blocking.md) a [rozhraní Windows Sockets: pořadí bajtů](../mfc/windows-sockets-byte-ordering.md).

Pokud používáte nebo odvozen od třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), budete muset spravovat tyto problémy sami. Pokud používáte nebo odvozen od třídy [csocket –](../mfc/reference/csocket-class.md), knihovna MFC je spravuje za vás.

## <a name="converting-strings"></a>Převádění řetězců

Pokud komunikaci mezi aplikací, které používají řetězce uložené v různých formátech širokého znaku, například ve formátu Unicode nebo vícebajtový znak sad (MBCS), nebo mezi jedním z nich a aplikace pomocí řetězce znaků ANSI, je třeba spravovat převody sami podle `CAsyncSocket`. `CArchive` Objekt použitý s `CSocket` objekt spravuje tohoto převodu můžete prostřednictvím možností třídy [CString](../atl-mfc-shared/reference/cstringt-class.md). Další informace najdete v tématu Specifikace rozhraní Windows Sockets, nachází v sadě Windows SDK.

Další informace naleznete v tématu:

- [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sokety streamu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)

