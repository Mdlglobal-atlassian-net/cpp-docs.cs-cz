---
title: Úložiště adres
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 47b09ab6cd0b2045206daaee4badad32858ff934
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336189"
---
# <a name="storage-of-addresses"></a>Úložiště adres

Velikost úložiště potřebná pro adresu a její význam závisí na implementaci kompilátoru. Není zaručeno, že ukazatele na různé typy budou mít stejnou délku. Proto je **sizeof (Char \*)** nutně rovno **sizeof ( \*int)**.

**Specifické pro Microsoft**

Pro kompilátor jazyka Microsoft C je **sizeof (Char \*)** rovno **sizeof ( \*int)**.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Deklarace ukazatelů](../c-language/pointer-declarations.md)
