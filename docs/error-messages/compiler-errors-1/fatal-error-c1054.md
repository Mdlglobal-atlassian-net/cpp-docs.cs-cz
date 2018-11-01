---
title: Závažná chyba C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: 0bfd0c03378b1a9c616a014ac96153b3ab04af9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569196"
---
# <a name="fatal-error-c1054"></a>Závažná chyba C1054

limit kompilátoru: Inicializátory jsou vnořené moc hluboko

Kód překračuje limit vnoření v inicializátorech (v závislosti na kombinaci typů, který je inicializován úrovně 10 až 15).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Zjednodušení datové typy, které během inicializace ke snížení vnoření.

1. Po deklaraci inicializujte proměnné v samostatných příkazů.