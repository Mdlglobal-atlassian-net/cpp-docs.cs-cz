---
title: "Upozornění linkerů Lnk4206 | Microsoft Docs"
ms.date: 12/05/2017
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4206
dev_langs: C++
helpviewer_keywords: LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cd13ac59aefa074db869f0502743c7a49d23082c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4206"></a>Upozornění linkerů LNK4206

> informace o předkompilovaných typu nebyl nalezen. '*filename*' není propojené nebo přepsána; propojování objektů, jako kdyby žádné informace o ladění

*Filename* souboru objektu, kompilovat s použitím [/Yc](../../build/reference/yc-create-precompiled-header-file.md), nebyl zadaný v příkazu odkaz nebo byl přepsán.

Běžný scénář pro toto upozornění je po .obj, který byl kompilován s /Yc v knihovně, a tam, kde neexistují žádné symbol odkazy na tento .obj z vašeho kódu.  V takovém případě linkeru nebude používat (nebo i v tématu) souboru .obj.  V takovém případě by měl znovu zkompiluje kód a použít [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) pro objekty zkompilovat pomocí [/Yu](../../build/reference/yu-use-precompiled-header-file.md).