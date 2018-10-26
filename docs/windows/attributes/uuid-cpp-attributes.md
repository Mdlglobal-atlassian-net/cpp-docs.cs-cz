---
title: UUID (atributy C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.uuid
dev_langs:
- C++
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3eddf1981aba8babcb87562ed546ce4086499fd7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071336"
---
# <a name="uuid-c-attributes"></a>uuid (atributy C++)

Určuje jedinečné ID pro třídu nebo rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>Parametry

*uuid*<br/>
128-bit, jedinečný identifikátor.

## <a name="remarks"></a>Poznámky

Pokud není zadán definici třídy nebo rozhraní **uuid** atribut C++ a kompilátor Visual C++ bude poskytovat jednu. Pokud zadáte **uuid**, musí obsahovat uvozovky.

Pokud nezadáte **uuid**, pak bude kompilátor generovat stejný identifikátor GUID pro rozhraní nebo třídy se stejným názvem v projektech různých atributů v počítači.

Uuidgen.exe nebo Guidgen.exe můžete použít ke generování vlastní jedinečné ID. (Chcete-li spustit některý z těchto nástrojů, klikněte na tlačítko **Start** a klikněte na tlačítko **spustit** v nabídce. Zadejte název požadované nástroje.)

Při použití v projektu, která ATL také nepoužívá, určení **uuid** atribut je stejné jako zadání [uuid](../../cpp/uuid-cpp.md) **__declspec** modifikátor. Načíst **uuid** třídy, můžete použít [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Příklad

Najdete v článku [umožňujících vazbu](bindable.md) příklad ukázkový používání **uuid**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **struktura**, **rozhraní**, **sjednocení**, **výčtu**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/desktop/Midl/uuid)