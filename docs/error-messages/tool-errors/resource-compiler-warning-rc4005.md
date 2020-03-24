---
title: Upozornění kompilátoru prostředků RC4005
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: c428fefa90cceed6a8bc9b7f6e4b95ec2db5e039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182406"
---
# <a name="resource-compiler-warning-rc4005"></a>Upozornění kompilátoru prostředků RC4005

' identifier ': předefinování makra

Identifikátor je definován dvakrát. Kompilátor použil druhou definici makra.

Toto upozornění může být způsobeno definováním makra na příkazovém řádku a v kódu s direktivou `#define`. Může to být také způsobeno makry importovanými ze souborů include.

Chcete-li odstranit upozornění, buď odstraňte jednu z definic nebo použijte `#undef` direktivu před druhou definicí.
