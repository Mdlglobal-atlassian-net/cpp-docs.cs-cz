---
title: Závažná chyba C1005 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1005
dev_langs:
- C++
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 888bdaf2eaddc0d4178affa1ccc4ae77c34f4617
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092307"
---
# <a name="fatal-error-c1005"></a>Závažná chyba C1005

řetězec je moc velký pro vyrovnávací paměť

Řetězec v zprostředkující soubor kompilátoru došlo k přetečení vyrovnávací paměti.

Tuto chybu můžete narazit při parametr předat buď [/Fd](../../build/reference/fd-program-database-file-name.md) nebo [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) – možnosti kompilátoru je větší než 256 bajtů.