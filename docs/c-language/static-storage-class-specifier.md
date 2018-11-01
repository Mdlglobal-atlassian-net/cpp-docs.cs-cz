---
title: Statický specifikátor třídy úložiště
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: 2596e257ae6e22e207451b97b0361aecdfffba03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594035"
---
# <a name="static-storage-class-specifier"></a>Statický specifikátor třídy úložiště

Proměnná deklarovaná na vnitřní úrovni **statické** – specifikátor třídy úložiště má globální dobu platnosti, ale je viditelný pouze v rámci bloku ve kterém je deklarována. Pro konstantní řetězce je použití **statické** je užitečné, protože zmírňuje režii časté inicializace v často volaných funkcích.

## <a name="remarks"></a>Poznámky

Pokud neinicializujete explicitně **statické** proměnné, je inicializován na 0 ve výchozím nastavení. Uvnitř funkce **statické** způsobí, že je přiděleno úložiště a slouží jako definice. Vnitřní statické proměnné poskytují trvalé soukromé úložiště, které je viditelné pouze jedinou funkcí.

## <a name="see-also"></a>Viz také

[Třídy úložiště jazyka C](c-storage-classes.md)<br/>
[Třídy úložiště (C++)](../cpp/storage-classes-cpp.md)