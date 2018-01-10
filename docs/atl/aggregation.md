---
title: Agregace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8dbb0332bc7e55464e5b8af9d0b57e236f23dc86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="aggregation"></a>Agregace
Existují situace, když uživatel provádějící implementaci objektu chcete využít výhod služeb, které jiné, předem objektu. Kromě toho přeje tento druhý objekt zobrazí jako přirozené součást první. COM dosahuje obou těchto cílů prostřednictvím členství ve skupině a agregaci.  
  
 Agregace znamená, že objekt obsahující (vnějšího) vytvoří objekt obsažené (vnitřního) jako součást procesu její vytvoření a jsou vystaveny vnější rozhraní vnitřní objekt. Objekt umožňuje samotné být agregovatelné, nebo ne. Pokud se jedná, musí ho podle určitá pravidla za účelem agregace správně fungovat.  
  
 Především se stává, všechny **IUnknown** volání metod na obsažený objekt musí delegovat na objekt obsahující.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM](../atl/introduction-to-com.md)   
 [Opětovné použití objektů](http://msdn.microsoft.com/library/windows/desktop/ms678443)

