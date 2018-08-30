---
title: Práce s vlákny (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.threading
dev_langs:
- C++
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19f49951cad65d3dbf15c406af9ac78a28408d4b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221811"
---
# <a name="threading-c"></a>threading (C++)

Určuje model vláken pro objekt modelu COM.

## <a name="syntax"></a>Syntaxe

```cpp
[ threading(
   model=enumeration
) ]
```

### <a name="parameters"></a>Parametry

*model* (volitelné)  
Jeden z následujících modely dělení na vlákna:

- `apartment` (podprocesový model apartment)

- `neutral` (Součásti rozhraní .NET framework bez uživatelského rozhraní)

- `single` (jednoduché dělení na vlákna)

- `free` (bez vláken)

- `both` (objektu apartment a volných vláken)

Výchozí hodnota je `apartment`.

## <a name="remarks"></a>Poznámky

**Dělení na vlákna** C++ atribut se nezobrazují v souboru IDL vygenerovaný, ale budou použity v implementaci váš objekt modelu COM.

V projektech ATL Pokud [coclass](../windows/coclass.md) atribut je také k dispozici, model vláken určené *modelu* je předán jako parametr šablony [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) třídy , Vložit `coclass` atribut.

**Dělení na vlákna** atribut také chrání přístup k [event_source](../windows/event-source.md).

## <a name="example"></a>Příklad

Najdete v článku [licenci](../windows/licensed.md) příklad ukázkový používání **dělení na vlákna**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|**coclass**|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[COM – atributy](../windows/com-attributes.md)  
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Atributy třídy](../windows/class-attributes.md)  
[Podpora multithreadingu ve starším kódu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)  
[Neutrální bytů](/windows/desktop/cossdk/neutral-apartments)  