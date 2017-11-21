---
title: "pár (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::pair
dev_langs: C++
helpviewer_keywords: pair class [STL/CLR]
ms.assetid: 3326b4d9-a52a-49e5-8103-9aa5e8b352de
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ca6ee4a44ea9e126be16b785b9ae52c7a852bc5e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pair-stlclr"></a>pair (STL/CLR)
Šablony třídy popisuje objekt, který zabalí dvojici hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### <a name="parameters"></a>Parametry  
 value1  
 Typ první zabalená hodnota.  
  
 Value2  
 Typ druhého zabalená hodnota.  
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[Pair::first_type (STL/CLR)](../dotnet/pair-first-type-stl-clr.md)|Typ první zabalená hodnota.|  
|[Pair::second_type (STL/CLR)](../dotnet/pair-second-type-stl-clr.md)|Typ druhého zabalená hodnota.|  
  
|Člen objektu|Popis|  
|-------------------|-----------------|  
|[Pair::First (STL/CLR)](../dotnet/pair-first-stl-clr.md)|První uložené hodnotu.|  
|[Pair::Second (STL/CLR)](../dotnet/pair-second-stl-clr.md)|Druhá hodnota uložené.|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[Pair::Pair (STL/CLR)](../dotnet/pair-pair-stl-clr.md)|Vytvoří objekt dvojice.|  
|[Pair::swap (STL/CLR)](../dotnet/pair-swap-stl-clr.md)|Zamění obsah dvě dvojice.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[Pair::Operator = (STL/CLR)](../dotnet/pair-operator-assign-stl-clr.md)|Nahradí uložené dvojice hodnot.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt ukládá dvojici hodnot. Tato třída šablony slouží ke kombinování dvou hodnot do jednoho objektu. Všimněte si, že `cliext::pair` (zde popsané) ukládá pouze spravované typy; k uložení pár nespravované typy využívají `std::pair`, deklarované v `<utility>`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / nástroj >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [make_pair – (STL/CLR)](../dotnet/make-pair-stl-clr.md)