---
title: Úložiště adres | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fe77d3775c489399bb8b9032e645eee17d70b0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076590"
---
# <a name="storage-of-addresses"></a>Úložiště adres

Velikost úložiště potřebná pro adresu a její význam závisí na implementaci kompilátoru. Není zaručeno, že ukazatele na různé typy budou mít stejnou délku. Proto **sizeof (char \*)** , nemusí být nutně roven **sizeof (int \*)**.

**Specifické pro Microsoft**

Kompilátor Microsoft C **sizeof (char \*)** rovná **sizeof (int \*)**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Deklarace ukazatelů](../c-language/pointer-declarations.md)