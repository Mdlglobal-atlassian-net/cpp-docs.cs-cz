---
title: "Požadavky na elementy kontejnerů STL/CLR | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f12bc8c3a6e2ecaa544ab5bbe875cc2ae358ef3a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="requirements-for-stlclr-container-elements"></a>Požadavky na elementy kontejnerů STL/CLR
Všechny odkazové typy, které jsou vloženy do kontejnerů STL/CLR musí mít minimálně následující prvky:  
  
-   Veřejné kopírovacího konstruktoru.  
  
-   Operátor veřejné přiřazení.  
  
-   Veřejné destruktor.  
  
 Kromě toho asociativní kontejnery, jako [nastavit](../dotnet/set-stl-clr.md) a [mapy](../dotnet/map-stl-clr.md) musí mít veřejný relační operátor definované, což je `operator<` ve výchozím nastavení. Některé operace kontejnerům může také vyžadovat veřejný výchozí konstruktor a veřejné ekvivalenční operátor být definován.  
  
 Jako odkazové typy, typy hodnot a obslužné rutiny, chcete-li typy, které se má být vložen do asociativní kontejneru musí mít operátor porovnání jako `operator<` definované. Požadavky na veřejné kopírovacího konstruktoru, operátor veřejné přiřazení a veřejné destruktor nejsou k dispozici pro typy hodnot nebo obslužné rutiny pro odkazové typy.  
  
## <a name="see-also"></a>Viz také  
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)