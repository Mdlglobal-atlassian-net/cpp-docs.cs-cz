---
title: Chyba linkerů Lnk1000 | Microsoft Docs
ms.custom: ''
ms.date: 06/18/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1000
dev_langs:
- C++
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a01db36200995813ec4b6862e9ddd04c6f069ba
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238679"
---
# <a name="linker-tools-error-lnk1000"></a>Chyba linkerů LNK1000

> Neznámá chyba; dokumentaci pro možnosti technické podpory

Poznámka: v případech chyby, a potom zkuste izolovat daný problém a vytvořit reprodukovatelnou testovacího případu. Informace o tom, jak prozkoumat a zprávy o těchto chybách naleznete v tématu [postup nahlásit problém s Visual C++ nástrojů nebo dokumentaci](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).

K této chybě může dojít, pokud zároveň standardní hlavičku soubory (například odkazující na Windows) a vlastní soubory. Zahrňte předkompilovaných hlaviček, pokud žádné, první a pak standardní hlavičky, za nímž následuje vlastní soubory hlaviček.