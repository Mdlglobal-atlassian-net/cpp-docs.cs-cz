---
title: Požadavky na elementy kontejnerů STL/CLR
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
ms.openlocfilehash: 0744d38a08dbd972b786e1cc74c112322ecf181f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428571"
---
# <a name="requirements-for-stlclr-container-elements"></a>Požadavky na elementy kontejnerů STL/CLR

Všechny typy odkazů, které jsou vloženy do kontejnerů STL/CLR musí mít minimálně následující prvky:

- Veřejné kopírovací konstruktor.

- Operátor přiřazení veřejné.

- Veřejným destruktorem.

Kromě toho asociativní kontejnery, jako [nastavit](../dotnet/set-stl-clr.md) a [mapy](../dotnet/map-stl-clr.md) musí mít veřejný operátor porovnání definované, což je `operator<` ve výchozím nastavení. Některé operace s kontejnery může vyžadovat také veřejný výchozí konstruktor a veřejný operátor rovnocennosti definovat.

Stejně jako typy odkazů, typy hodnot a popisovače odkazovat na typy, které mají být vloženy do asociativní kontejner musí mít operátor porovnání, jako `operator<` definované. Požadavky na veřejné kopírovacího konstruktoru, operátor přiřazení veřejné a veřejným destruktorem neexistují pro typy hodnot nebo popisovače referenční typy.

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)