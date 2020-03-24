---
title: Chyba kompilátoru C3661
ms.date: 11/04/2016
f1_keywords:
- C3661
helpviewer_keywords:
- C3661
ms.assetid: 50793fd1-1829-4b29-ad0d-094ef2068b43
ms.openlocfilehash: 5edda7eaf50dc4fca60f47128dc97de5d3a1a395
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200374"
---
# <a name="compiler-error-c3661"></a>Chyba kompilátoru C3661

seznam explicitních přepsání nenalezl žádné metody, které by bylo možné přepsat.

Explicitní přepsání určilo jeden nebo více názvů typů.  V těchto typech ale neexistovala žádná funkce s nezbytným podpisem, která se shodovala s signaturou překryté funkce.  Pokud se pokusíte přepsat na základě názvu typu, musí existovat jedna nebo více virtuálních funkcí v zadaném typu, které odpovídají podpisu přepsané funkce.

Další informace najdete v tématu [Explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).
