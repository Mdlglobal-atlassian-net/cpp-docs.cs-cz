---
title: Závažná chyba C1054 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1054
dev_langs:
- C++
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 439019b1f510127ae54e77d445d59e86be09a49b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101966"
---
# <a name="fatal-error-c1054"></a>Závažná chyba C1054

limit kompilátoru: Inicializátory jsou vnořené moc hluboko

Kód překračuje limit vnoření v inicializátorech (v závislosti na kombinaci typů, který je inicializován úrovně 10 až 15).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Zjednodušení datové typy, které během inicializace ke snížení vnoření.

1. Po deklaraci inicializujte proměnné v samostatných příkazů.