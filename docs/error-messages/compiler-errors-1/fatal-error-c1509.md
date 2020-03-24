---
title: Závažná chyba C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: 0d1d7255dd64239a6a76bb15a1f309b43eac0d4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202953"
---
# <a name="fatal-error-c1509"></a>Závažná chyba C1509

limit kompilátoru: ve funkci Function Function je moc velký počet stavů obslužných rutin výjimek. jednodušší funkce

Kód překračuje interní omezení pro stavy obslužné rutiny výjimek (32 768 stavy).

Nejběžnější příčinou je, že funkce obsahuje složitý výraz uživatelsky definovaných proměnných třídy a aritmetických operátorů.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Zjednodušte výrazy přiřazením běžných dílčích výrazů k dočasným proměnným.

1. Rozdělení funkce na menší funkce.
