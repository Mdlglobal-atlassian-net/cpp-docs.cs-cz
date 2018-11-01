---
title: Úložiště adres
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 2a0e218d4d34fa1482986ecccd7da8adba38086b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539370"
---
# <a name="storage-of-addresses"></a>Úložiště adres

Velikost úložiště potřebná pro adresu a její význam závisí na implementaci kompilátoru. Není zaručeno, že ukazatele na různé typy budou mít stejnou délku. Proto **sizeof (char \*)** , nemusí být nutně roven **sizeof (int \*)**.

**Specifické pro Microsoft**

Kompilátor Microsoft C **sizeof (char \*)** rovná **sizeof (int \*)**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Deklarace ukazatelů](../c-language/pointer-declarations.md)