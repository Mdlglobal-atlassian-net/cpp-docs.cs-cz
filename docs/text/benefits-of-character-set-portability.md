---
title: Výhody znakové sady přenositelnost | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 115a4524f3b11d847291015f3bee5ca10f628310
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423439"
---
# <a name="benefits-of-character-set-portability"></a>Výhody přenositelnosti znakové sady

Můžete využívat výhody funkce MFC a C za běhu přenositelnost i v případě, že jste nemáte v úmyslu aktuálně internationalizi vaší aplikace:

- Kódování přenositelnosti dělá váš kód základní flexibilní. Můžete později přesunout ho snadno kódování Unicode a MBCS.

- Použití kódování Unicode je vaše aplikace pro Windows efektivnější. Vzhledem k tomu Windows používá kódování Unicode, kódování Unicode řetězce předané do a z operačního systému musí být převedeny, což zahrnuje režii.


## <a name="see-also"></a>Viz také

[Unicode a MBCS](../text/unicode-and-mbcs.md)<br/>
[Podpora pro Unicode](../text/support-for-unicode.md)