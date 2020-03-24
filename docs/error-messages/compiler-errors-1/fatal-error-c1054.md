---
title: Závažná chyba C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: d094d0892d43a5f9894f03538f72e59b57bad6db
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204461"
---
# <a name="fatal-error-c1054"></a>Závažná chyba C1054

limit kompilátoru: Inicializátory jsou vnořené moc hluboko.

Kód překračuje omezení vnořování u inicializátorů (10-15 úrovní v závislosti na kombinaci typů, které jsou inicializovány).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Zjednodušte typy dat, které jsou inicializovány pro omezení vnořování.

1. Inicializovat proměnné v samostatných příkazech po deklaraci.
