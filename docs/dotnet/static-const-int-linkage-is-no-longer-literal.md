---
title: Statické propojení Const Int už není literál | Dokumentace Microsoftu
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
ms.openlocfilehash: c51853274b061ba290ff90993f45ccdf3375349b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431291"
---
# <a name="static-const-int-linkage-is-no-longer-literal"></a>Statické propojení Const Int už není literál

Deklarace konstantní členské třídy změnil ze spravovaného rozšíření jazyka C++ pro Visual C++.

I když `static const` integrální členy jsou stále podporovány, jejich propojení atribut byl změněn. Atribut jejich předchozího propojení se provádí v literálu celočíselný člen. Představte si třeba následující spravovaných rozšíření třídy:

```
public __gc class Constants {
public:
   static const int LOG_DEBUG = 4;
};
```

Tím se vytvoří následující soubor CIL se NAČTE základní atributy pole (Poznámka: atribut literálu):

```
.field public static literal int32
modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)
```

Když to stále zkompiluje v nové syntaxi:

```
public ref class Constants {
public:
   static const int LOG_DEBUG = 4;
};
```

už generuje atribut literálu a proto není zobrazen jako konstantu. modul CLR Runtime:

```
.field public static int32 modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)
```

Pokud chcete mít stejný atribut literálu mezi jazyk, deklarace by měla být změněna na nově podporované `literal` datový člen, následujícím způsobem,

```
public ref class Constants {
public:
   literal int LOG_DEBUG = 4;
};
```

## <a name="see-also"></a>Viz také

[Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[literál](../windows/literal-cpp-component-extensions.md)