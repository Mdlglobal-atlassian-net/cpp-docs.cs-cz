---
title: uuid (atributy C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: c507a9ae42afc5081c290d38464aa7f24c277d15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166117"
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
128 jedinečný identifikátor.

## <a name="remarks"></a>Poznámky

Pokud definice rozhraní nebo třídy neurčuje atribut **UUID** C++ , kompilátor společnosti Microsoft C++ ho poskytne. Pokud zadáte **identifikátor UUID**, je nutné zahrnout uvozovky.

Pokud neurčíte **UUID**, kompilátor vygeneruje stejný identifikátor GUID pro rozhraní nebo třídy se stejným názvem v projektech různých atributů v počítači.

K vygenerování vlastních jedinečných ID můžete použít Uuidgen. exe nebo Guidgen. exe. (Chcete-li spustit některý z těchto nástrojů, klikněte na tlačítko **Start** a v nabídce klikněte na příkaz **Spustit** . Pak zadejte název požadovaného nástroje.)

Při použití v projektu, který nepoužívá také ATL, je zadání atributu **UUID** stejné jako při zadání modifikátoru __declspec [identifikátoru UUID](../../cpp/uuid-cpp.md) **__declspec** . Chcete-li načíst **UUID** třídy, můžete použít [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>Příklad

Ukázku použití **identifikátoru UUID**získáte v příkladu s možností [vazby](bindable.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**, **rozhraní**, **sjednocení**, **výčet**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)
