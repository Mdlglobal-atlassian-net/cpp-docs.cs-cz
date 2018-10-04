---
title: (C++ COM atribut ProgID) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5e499a6faabda20450a7af76d97664b90464b36
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789326"
---
# <a name="progid"></a>progid

Určuje identifikátor pro objekt modelu COM ProgID.

## <a name="syntax"></a>Syntaxe

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Parametry

*Jméno*<br/>
Identifikátor ProgID reprezentující objekt.

ProgID prezentovat čitelná verze identifikátor třídy (CLSID) slouží k identifikaci objektů modelu COM a ActiveX.

## <a name="remarks"></a>Poznámky

**Progid** atribut C++ umožňuje zadat klíč pro objekt modelu COM ProgID. Identifikátor ProgID má tvar *name1.name2.version*. Pokud nezadáte *verze* pro ProgID, je výchozí verze 1. Pokud nezadáte *name1.name2*, výchozí název je *classname.classname*. Pokud nezadáte **progid** a zadáte `vi_progid`, *name1.name2* pocházejí ze `vi_progid` (Další pořadové číslo) a verze se připojí.

Pokud blok atribut, který používá **progid** také nepoužívá **uuid**, kompilátor zkontroluje registru a zjistěte, jestli **uuid** existuje pro zadaný rozbočovač **progid** . Pokud **progid** není zadán, verze (a název coclass, pokud vytváříte coclass) se použije k vygenerování **progid**.

**ProgID** znamená `coclass` atribut, to znamená, pokud zadáte **progid**, je totéž jako zadání `coclass` a **progid** atributy.

**Progid** atribut způsobí, že třída má být automaticky zaregistrován se zadaným názvem. Nebudou se zobrazovat generovaného souboru **progid** hodnotu.

Pokud tento atribut se používá v rámci projektu, který používá knihovny ATL, se změní chování atributu. Kromě výše uvedené chování je používán informace zadané pomocí tohoto atributu `GetProgID` funkce vloženy `coclass` atribut. Další informace najdete v tématu [coclass](coclass.md) atribut.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [coclass](coclass.md) ukázkový používání **progid**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Klíč progID](/windows/desktop/com/-progid--key)  
