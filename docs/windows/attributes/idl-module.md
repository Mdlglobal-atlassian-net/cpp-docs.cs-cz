---
title: možnost idl_module (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_module
dev_langs:
- C++
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91bed0ebfdacae21f2d606c0b8fa1bb43326816d
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789542"
---
# <a name="idlmodule"></a>idl_module

Určuje vstupní bod v souboru .dll.

## <a name="syntax"></a>Syntaxe

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>Parametry

*Jméno*<br/>
Uživatelem definovaný název pro blok kódu, který se zobrazí v souboru IDL.

*NázevSouboru*<br/>
(Volitelné) Soubor .dll, který obsahuje exportu.

*uuid*<br/>
(Volitelné) Jedinečný identifikátor.

*helpstring*<br/>
(Volitelné) Znakový řetězec používaný k popisu knihovny typů.

*helpstringcontext*<br/>
(Volitelné) ID tématu nápovědy HLP nebo CHM souboru.

*helpcontext*<br/>
(Volitelné) ID nápovědy pro tuto knihovnu typů.

*hidden*<br/>
(Volitelné) Parametr, který zabraňuje zobrazení knihovny. Zobrazit [skryté](/windows/desktop/Midl/hidden) atribut MIDL pro další informace.

*restricted*<br/>
(Volitelné) Členové knihovny nejde volat libovolně. Zobrazit [s omezeným přístupem](/windows/desktop/Midl/restricted) atribut MIDL pro další informace.

*deklarace funkce*<br/>
Funkce, která budou definovat.

## <a name="remarks"></a>Poznámky

**Možnost idl_module** atribut C++ umožňuje zadat vstupní bod v souboru .dll, který umožňuje importovat ze souboru .dll.

**Možnost idl_module** atribut má podobné funkce [modulu](/windows/desktop/Midl/module) atribut MIDL.

Všechno můžete exportovat z objektu COM, který můžete exportovat z soubor DLL tak, že vložíte vstupní bod knihovny DLL v bloku knihovny ze souboru IDL.

Vaše musí používat **možnost idl_module** ve dvou krocích. Nejprve je nutné definovat dvojici název/DLL. Poté, kdy použít **možnost idl_module** k určení vstupního bodu, zadejte název a další atributy.

## <a name="example"></a>Příklad

Následující kód ukazuje způsob použití **možnost idl_module** atribut:

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Kdekoli|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[entry](entry.md)  