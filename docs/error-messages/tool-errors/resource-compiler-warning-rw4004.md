---
title: Upozornění kompilátoru prostředků RW4004 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33305f1f86c0cc1722e4a235ec27927f6e70675f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095986"
---
# <a name="resource-compiler-warning-rw4004"></a>Upozornění kompilátoru prostředků RW4004

Virtuální klíče kódu není ekvivalentní znaku standardu ASCII

Řetězcový literál se použil pro virtuální kód v akcelerátoru typ VIRTKEY.

Toto upozornění můžete pokračovat, ale mějte na paměti, že akcelerátor klíčů vygenerovaných nemusí odpovídat řetězec, který jste určili. (VIRTKEYs použít různé kódy kláves než ASCII akcelerátory.)

Řetězcové literály jsou syntakticky správný, je jenom zajistit, že dostanete akcelerátoru pomocí **jich\* #define** hodnoty v WINDOWS.h.