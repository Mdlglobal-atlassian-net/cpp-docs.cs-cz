---
title: Upozornění kompilátoru prostředků RW4004
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: bafd1084a665fc656fe184064a48e5fffc61c957
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346077"
---
# <a name="resource-compiler-warning-rw4004"></a>Upozornění kompilátoru prostředků RW4004

Virtuální klíče kódu není ekvivalentní znaku standardu ASCII

Řetězcový literál se použil pro virtuální kód v akcelerátoru typ VIRTKEY.

Toto upozornění můžete pokračovat, ale mějte na paměti, že akcelerátor klíčů vygenerovaných nemusí odpovídat řetězec, který jste určili. (VIRTKEYs použít různé kódy kláves než ASCII akcelerátory.)

Řetězcové literály jsou syntakticky správný, je jenom zajistit, že dostanete akcelerátoru pomocí **jich\* #define** hodnoty v WINDOWS.h.