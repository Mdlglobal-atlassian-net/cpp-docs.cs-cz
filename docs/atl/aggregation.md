---
title: Agregace
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 288af427bd6a8d9baf572dfad8e4a25452694ad9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491971"
---
# <a name="aggregation"></a>Agregace

Existují situace, kdy by implementátor objektu mohl využívat služby nabízené jiným, předem vytvořeným objektem. Kromě toho by se měl tento druhý objekt zobrazit jako přirozené součásti prvního. COM dosahuje obou těchto cílů prostřednictvím zahrnutí a agregace.

Agregace znamená, že nadřazený objekt (vnější) vytvoří objekt obsažený (vnitřní) v rámci procesu vytváření a rozhraní vnitřního objektu jsou vystavena vnějším. Objekt umožňuje agregaci nebo nikoli. Pokud je, musí se při správné funkci agregace řídit určitá pravidla, aby správně fungovala.

Primárně musí všechna `IUnknown` volání metod na objektu, který ho obsahuje, delegovat na obsažený objekt.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Znovu použití objektů](/windows/win32/com/reusing-objects)
