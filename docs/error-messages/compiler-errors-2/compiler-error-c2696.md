---
title: Compiler Error C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 340a5d0596160b6c9c7bcfc78aed812f8c5f3fa3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367600"
---
# <a name="compiler-error-c2696"></a>Compiler Error C2696

Nelze vytvořit dočasný objekt spravovaného typu 'type'

Odkazy na `const` v nespravované aplikaci způsobit, že kompilátor volání konstruktoru a vytvořit dočasný objekt v zásobníku. Ale spravovanou třídu nikdy se dají vytvořit na zásobníku.

C2696 dosažitelný pouze pomocí možnosti kompilátoru zastaralé **oldSyntax**.
