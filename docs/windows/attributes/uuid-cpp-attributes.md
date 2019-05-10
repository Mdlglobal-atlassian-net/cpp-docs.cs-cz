---
title: uuid (atributy C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: eae79f9a4d0af6375834c0792c4004f52a16e07e
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448925"
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

Pokud není zadán definici třídy nebo rozhraní **uuid** C++ atribut, pak Microsoft C++ kompilátor bude poskytovat jednu. Pokud zadáte **uuid**, musí obsahovat uvozovky.

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
|**Neplatné atributy**|Žádný|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/desktop/Midl/uuid)