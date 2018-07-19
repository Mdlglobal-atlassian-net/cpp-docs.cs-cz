---
title: __based – gramatika | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad00244be53a2eebe4a02b99c6368333f3daf23
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939361"
---
# <a name="based-grammar"></a>__based – gramatika
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Na základě adresování je užitečné, když je nutné mít naprostou kontrolu nad segment, ve kterém jsou objekty přidělovány (statické a dynamické na základě dat).  
  
 Jedinou formou adresování podle přijatelný v 32bitových a 64bitových kompilacích je "na základě ukazatel", který definuje typ, který obsahuje 32bitové nebo 64bitové posunutí se základní 32bitová nebo 64bitová verze nebo na základě **void**.  
  
## <a name="grammar"></a>Gramatika  
 *na základě modifikátoru rozsahu*:  
 **__based (***výraz base***)**   
  
 *výraz Base*:  
 *Based-variablebased-Abstract-declaratorsegment-namesegment-CAST*  
  
 *na základě proměnná*:  
 *identifikátor*  
  
 *na základě abstraktní declarator*:  
 *abstraktní deklarátor*  
  
 *Základní typ*:  
 *Název typu*  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Základní ukazatele](../cpp/based-pointers-cpp.md)