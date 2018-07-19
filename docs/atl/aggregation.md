---
title: Agregace | Dokumentace Microsoftu
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
ms.openlocfilehash: 2457d6e94677c43985cadf8ca49a176a82566b6a
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37847866"
---
# <a name="aggregation"></a>Agregace
Existují situace, kdy implementátor objektu chtěli využívat služby nabízené objektem jiného, předem připravené. Kromě toho je vhodné tento druhý objekt jako přirozenou součástí první. COM dosahuje oba z těchto cílů prostřednictvím členství ve skupině a agregaci.  
  
 Agregace znamená, že nadřazený objekt (vnějšího) vytvoří obsaženého objektu (vnitřní) jako součást procesu vytváření a rozhraní vnitřní objekt jsou viditelné ve vnější. Objekt umožňuje sám být agregovatelné, nebo ne. Pokud se jedná, pak musí podstoupit určitá pravidla pro agregaci fungovala správně.  
  
 Především, všechny `IUnknown` volání metod na obsaženého objektu musí delegovat do obsahujícího objektu.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM](../atl/introduction-to-com.md)   
 [Opětovné použití objektů](http://msdn.microsoft.com/library/windows/desktop/ms678443)

