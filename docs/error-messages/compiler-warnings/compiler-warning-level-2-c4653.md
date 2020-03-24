---
title: Upozornění kompilátoru (úroveň 2) C4653
ms.date: 11/04/2016
f1_keywords:
- C4653
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
ms.openlocfilehash: 994e9a4963e7e10af2313b3dcea5bb8b2b93426e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161734"
---
# <a name="compiler-warning-level-2-c4653"></a>Upozornění kompilátoru (úroveň 2) C4653

možnost kompilátoru Option je nekonzistentní s předkompilovanou hlavičkou. aktuální možnost příkazového řádku se ignoruje.

Možnost zadaná s možností použití předkompilovaných hlaviček ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) byla nekonzistentní s možnostmi určenými při vytváření předkompilované hlavičky. Tato kompilace použila možnost zadanou při vytváření předkompilované hlavičky.

Toto upozornění může nastat, pokud byla při kompilaci předkompilované hlavičky zadána odlišná hodnota pro možnost struktury sady ([/zp](../../build/reference/zp-struct-member-alignment.md)).
