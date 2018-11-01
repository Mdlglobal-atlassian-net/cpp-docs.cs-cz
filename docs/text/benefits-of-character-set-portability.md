---
title: Výhody přenositelnosti znakové sady
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
ms.openlocfilehash: 446d59fe62999e5be652be5efabb53fd907fcd88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631345"
---
# <a name="benefits-of-character-set-portability"></a>Výhody přenositelnosti znakové sady

Můžete využívat výhody funkce MFC a C za běhu přenositelnost i v případě, že jste nemáte v úmyslu aktuálně internationalizi vaší aplikace:

- Kódování přenositelnosti dělá váš kód základní flexibilní. Můžete později přesunout ho snadno kódování Unicode a MBCS.

- Použití kódování Unicode je vaše aplikace pro Windows efektivnější. Vzhledem k tomu Windows používá kódování Unicode, kódování Unicode řetězce předané do a z operačního systému musí být převedeny, což zahrnuje režii.

## <a name="see-also"></a>Viz také

[Unicode a MBCS](../text/unicode-and-mbcs.md)<br/>
[Podpora pro Unicode](../text/support-for-unicode.md)