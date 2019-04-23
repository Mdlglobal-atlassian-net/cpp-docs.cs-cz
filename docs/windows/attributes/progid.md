---
title: ProgID (atribut COM jazyka C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: 5b0c688ad4d9b607cc1f5fb6b1c6d536a1c7888e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031127"
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
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Klíč progID](/windows/desktop/com/-progid--key)
