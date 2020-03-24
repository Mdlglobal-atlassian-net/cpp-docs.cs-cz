---
title: Upozornění linkerů LNK4001
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: d9659b0cf372ff8ebc225b890fb68866872bb3d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194405"
---
# <a name="linker-tools-warning-lnk4001"></a>Upozornění linkerů LNK4001

nebyly zadány žádné soubory objektů; používané knihovny

Linker předal jeden nebo více souborů. lib, ale žádné soubory. obj.

Vzhledem k tomu, že linker nemá přístup k informacím v souboru. lib, ke kterému je schopný přistupovat v souboru. obj, toto upozornění indikuje, že budete muset explicitně zadat další možnosti linkeru. Například může být nutné zadat možnosti [/Machine](../../build/reference/machine-specify-target-platform.md), [/out](../../build/reference/out-output-file-name.md)nebo [/entry](../../build/reference/entry-entry-point-symbol.md) .
