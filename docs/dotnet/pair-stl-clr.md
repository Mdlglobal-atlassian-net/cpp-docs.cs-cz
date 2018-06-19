---
title: pár (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::pair
dev_langs:
- C++
helpviewer_keywords:
- pair class [STL/CLR]
ms.assetid: 3326b4d9-a52a-49e5-8103-9aa5e8b352de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2d05dceaa763f8d0e33ccc86e783f66447c48b76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33160820"
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
|[pair::first_type (STL/CLR)](../dotnet/pair-first-type-stl-clr.md)|Typ první zabalená hodnota.|  
|[pair::second_type (STL/CLR)](../dotnet/pair-second-type-stl-clr.md)|Typ druhého zabalená hodnota.|  
  
|Člen objektu|Popis|  
|-------------------|-----------------|  
|[pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)|První uložené hodnotu.|  
|[pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)|Druhá hodnota uložené.|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[pair::pair (STL/CLR)](../dotnet/pair-pair-stl-clr.md)|Vytvoří objekt dvojice.|  
|[pair::swap (STL/CLR)](../dotnet/pair-swap-stl-clr.md)|Zamění obsah dvě dvojice.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[pair::operator= (STL/CLR)](../dotnet/pair-operator-assign-stl-clr.md)|Nahradí uložené dvojice hodnot.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt ukládá dvojici hodnot. Tato třída šablony slouží ke kombinování dvou hodnot do jednoho objektu. Všimněte si, že `cliext::pair` (zde popsané) ukládá pouze spravované typy; k uložení pár nespravované typy využívají `std::pair`, deklarované v `<utility>`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / nástroj >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [make_pair (STL/CLR)](../dotnet/make-pair-stl-clr.md)