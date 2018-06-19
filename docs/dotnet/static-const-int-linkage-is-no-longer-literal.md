---
title: Statické propojení Const Int už není literál | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- literal attribute [C++]
- constants, declaring
- integral constant expressions
ms.assetid: d2a5e3d2-ffb0-4b61-8114-bec5993a1195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cc3f72080c08807026c6458979ac0ba561e298df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164993"
---
# <a name="static-const-int-linkage-is-no-longer-literal"></a>Statické propojení Const Int už není literál
Deklarace konstantní člena třídy se změnila ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 I když `static const` integrační členové jsou stále podporovány, došlo ke změně atributu jejich propojení. Jejich dřívější propojený atribut se provádí členem celočíselný literál. Zvažte například následující spravovaných rozšíření třídy:  
  
```  
public __gc class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 To vytváří následující základní soubor CIL atributy pole (Poznámka: atribut literálu):  
  
```  
.field public static literal int32   
modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 Když to stále kompiluje pod nové syntaxe:  
  
```  
public ref class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 už vysílá atribut literálu a proto není zobrazen jako konstanta za běhu CLR:  
  
```  
.field public static int32 modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 Aby bylo možné používat stejný atribut literálu mezi jazyk, by mělo být změněno deklaraci do nově podporovaných `literal` – datový člen, následujícím způsobem,  
  
```  
public ref class Constants {  
public:  
   literal int LOG_DEBUG = 4;  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Deklarace členů v rámci třídy nebo rozhraní (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Literál](../windows/literal-cpp-component-extensions.md)