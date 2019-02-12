---
title: Úložiště adres
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 47b09ab6cd0b2045206daaee4badad32858ff934
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148735"
---
# <a name="storage-of-addresses"></a>Úložiště adres

Velikost úložiště potřebná pro adresu a její význam závisí na implementaci kompilátoru. Není zaručeno, že ukazatele na různé typy budou mít stejnou délku. Proto **sizeof (char \*)** , nemusí být nutně roven **sizeof (int \*)**.

**Microsoft Specific**

Kompilátor Microsoft C **sizeof (char \*)** rovná **sizeof (int \*)**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Deklarace ukazatelů](../c-language/pointer-declarations.md)
