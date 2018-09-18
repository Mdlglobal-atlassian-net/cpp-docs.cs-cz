---
title: Závažná chyba C1009 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1009
dev_langs:
- C++
helpviewer_keywords:
- C1009
ms.assetid: dcc8383c-3362-4c47-9c26-25d2451ebd53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1fbd8994be6fd86a764db400d8761a5d697079b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037330"
---
# <a name="fatal-error-c1009"></a>Závažná chyba C1009

limit kompilátoru: makra jsou vnořená moc hluboko

Kompilátor se pokusil rozšířit příliš mnoho makra ve stejnou dobu. Kompilátor může obsahovat maximálně 256 úrovní vnořených makra. Vnořené makra rozdělte jednodušší makra.