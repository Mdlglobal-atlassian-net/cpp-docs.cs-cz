---
title: Výhody přenositelnosti znakové sady
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
ms.openlocfilehash: 0ca7e46cabb2d98a64a244863f8574a3e9e2a456
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410772"
---
# <a name="benefits-of-character-set-portability"></a>Výhody přenositelnosti znakové sady

Můžete využívat výhody funkce MFC a C za běhu přenositelnost i v případě, že jste nemáte v úmyslu aktuálně internationalizi vaší aplikace:

- Kódování přenositelnosti dělá váš kód základní flexibilní. Můžete později přesunout ho snadno kódování Unicode a MBCS.

- Použití kódování Unicode je vaše aplikace pro Windows efektivnější. Vzhledem k tomu Windows používá kódování Unicode, kódování Unicode řetězce předané do a z operačního systému musí být převedeny, což zahrnuje režii.

## <a name="see-also"></a>Viz také:

[Unicode a MBCS](../text/unicode-and-mbcs.md)<br/>
[Podpora pro Unicode](../text/support-for-unicode.md)
