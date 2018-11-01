---
title: Chyba kompilátoru C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 340a5d0596160b6c9c7bcfc78aed812f8c5f3fa3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562864"
---
# <a name="compiler-error-c2696"></a>Chyba kompilátoru C2696

Nelze vytvořit dočasný objekt spravovaného typu 'type'

Odkazy na `const` v nespravované aplikaci způsobit, že kompilátor volání konstruktoru a vytvořit dočasný objekt v zásobníku. Ale spravovanou třídu nikdy se dají vytvořit na zásobníku.

C2696 dosažitelný pouze pomocí možnosti kompilátoru zastaralé **oldSyntax**.
