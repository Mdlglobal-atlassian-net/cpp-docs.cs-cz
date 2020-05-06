---
title: Nevhodný přístup ke sjednocení
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: 9fd7bdc753f6359a8760e58813f9009411c1bf44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326128"
---
# <a name="improper-access-to-a-union"></a>Nevhodný přístup ke sjednocení

**3.3.2.3 ANSI** K členu objektu Union je přistup přes člen jiného typu.

Pokud je deklarováno sjednocení dvou typů a je uložena jedna hodnota, ale sjednocení je dostupné s jiným typem, výsledky jsou nespolehlivé.

Například sjednocení typu **float** a `int` je deklarováno. Hodnota **typu float** je uložena, ale program později k hodnotě přistupuje jako `int`. V takové situaci bude hodnota záviset na interním úložišti hodnot **float** . Celočíselná hodnota by nebyla spolehlivá.

## <a name="see-also"></a>Viz také

[Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)
