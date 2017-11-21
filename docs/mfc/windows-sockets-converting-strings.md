---
title: "Windows Sockets: Převádění řetězců | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4b0b66cb83dc13f74e5417cab7f8cec0fe65b73a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets: Převádění řetězců
V tomto článku a dvě doprovodné články vysvětlují několik problémů v rozhraní Windows Sockets programování. Tento článek se zabývá převádění řetězců. Další problémy, které jsou popsané v [Windows Sockets: blokování](../mfc/windows-sockets-blocking.md) a [Windows Sockets: pořadí bajtů](../mfc/windows-sockets-byte-ordering.md).  
  
 Pokud používáte nebo odvozena od třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), budete muset řešení těchto problémů. Pokud používáte nebo odvozena od třídy [CSocket](../mfc/reference/csocket-class.md), spravuje MFC za vás.  
  
## <a name="converting-strings"></a>Převádění řetězců  
 Pokud komunikaci mezi aplikacemi, které používají řetězce uložené v různých formátech široká charakterová, například kódování Unicode nebo vícebajtových znaků nastaví (MBCS), nebo mezi jednu z těchto a aplikace pomocí znakových řetězců v kódu ANSI, musí spravovat převody sami podle `CAsyncSocket`. `CArchive` Objekt používaný s `CSocket` objekt spravuje tento převod můžete prostřednictvím možností třídy [CString](../atl-mfc-shared/reference/cstringt-class.md). Další informace najdete v tématu Specifikace rozhraní Windows Sockets, umístěný ve Windows SDK.  
  
 Další informace naleznete v tématu:  
  
-   [Windows Sockets: Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: pozadí](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Sokety datového proudu](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)

