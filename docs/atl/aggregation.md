---
title: Agregace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 760a595274ba7a1901138cc0cceceddf97122725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32353960"
---
# <a name="aggregation"></a>Agregace
Existují situace, když uživatel provádějící implementaci objektu chcete využít výhod služeb, které jiné, předem objektu. Kromě toho přeje tento druhý objekt zobrazí jako přirozené součást první. COM dosahuje obou těchto cílů prostřednictvím členství ve skupině a agregaci.  
  
 Agregace znamená, že objekt obsahující (vnějšího) vytvoří objekt obsažené (vnitřního) jako součást procesu její vytvoření a jsou vystaveny vnější rozhraní vnitřní objekt. Objekt umožňuje samotné být agregovatelné, nebo ne. Pokud se jedná, musí ho podle určitá pravidla za účelem agregace správně fungovat.  
  
 Především se stává, všechny **IUnknown** volání metod na obsažený objekt musí delegovat na objekt obsahující.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM](../atl/introduction-to-com.md)   
 [Opětovné použití objektů](http://msdn.microsoft.com/library/windows/desktop/ms678443)

