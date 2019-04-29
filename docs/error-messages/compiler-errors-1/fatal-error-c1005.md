---
title: Závažná chyba C1005
ms.date: 11/04/2016
f1_keywords:
- C1005
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
ms.openlocfilehash: a84791367656729b1cbd50ca180368f6c01531a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383188"
---
# <a name="fatal-error-c1005"></a>Závažná chyba C1005

řetězec je moc velký pro vyrovnávací paměť

Řetězec v zprostředkující soubor kompilátoru došlo k přetečení vyrovnávací paměti.

Tuto chybu můžete narazit při parametr předat buď [/Fd](../../build/reference/fd-program-database-file-name.md) nebo [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) – možnosti kompilátoru je větší než 256 bajtů.