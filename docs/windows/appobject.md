---
title: appobject – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.appobject
dev_langs:
- C++
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8de7bbfb2f00f5e1a909a83a5399e2d564747962
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213992"
---
# <a name="appobject"></a>appobject

Identifikuje coclass jako objekt aplikace, který je přidružen k aplikaci úplné .exe a označuje, že jsou globálně k dispozici v této funkce a vlastnosti třídy typu coclass [knihovny typů](../mfc/automation-clients-using-type-libraries.md).

## <a name="syntax"></a>Syntaxe

```cpp
[appobject]
```

## <a name="remarks"></a>Poznámky

**Appobject –** C++ atribut má stejné funkce jako [appobject –](/windows/desktop/Midl/appobject) atribut MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje předchází blok atribut, který obsahuje definici jednoduchou třídu **appobject –**:

```cpp
// cpp_attr_ref_appobject.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];

[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]
__interface ICustom {};

[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]
class A : public ICustom {
   int i;
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|`coclass`|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy třídy](../windows/class-attributes.md)  
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)  