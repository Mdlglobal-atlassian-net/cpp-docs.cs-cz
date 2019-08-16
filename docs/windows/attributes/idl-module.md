---
title: idl_module (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: 8838a833552ae7066dbcf17b4f676d6626c069f8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514672"
---
# <a name="idl_module"></a>idl_module

Určuje vstupní bod v souboru. dll.

## <a name="syntax"></a>Syntaxe

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>Parametry

*name*<br/>
Uživatelsky definovaný název pro blok kódu, který se zobrazí v souboru. idl.

*NázevSouboru*<br/>
Volitelné Soubor. dll, který obsahuje export.

*uuid*<br/>
Volitelné Jedinečné ID.

*helpstring*<br/>
Volitelné Řetězec znaků, který slouží k popisu knihovny typů.

*helpstringcontext*<br/>
Volitelné ID tématu nápovědy v souboru HLP nebo CHM.

*helpcontext*<br/>
Volitelné ID nápovědu pro tuto knihovnu typů

*hidden*<br/>
Volitelné Parametr, který brání zobrazení knihovny. Další informace [](/windows/win32/Midl/hidden) naleznete u skrytého atributu MIDL.

*restricted*<br/>
Volitelné Členy knihovny nelze libovolně volat. Další informace [](/windows/win32/Midl/restricted) naleznete u atributu Restricted MIDL.

*deklarace funkce*<br/>
Funkce, kterou budete definovat.

## <a name="remarks"></a>Poznámky

Atribut **idl_module** C++ umožňuje zadat vstupní bod v souboru. dll, který umožňuje import ze souboru. dll.

Atribut **idl_module** má podobné funkce jako u atributu [Module](/windows/win32/Midl/module) MIDL.

Můžete exportovat cokoli z objektu modelu COM, který lze exportovat ze souboru. dll tak, že umístíte vstupní bod knihovny DLL do bloku knihovny souboru. idl.

Vaše **idl_module** musí používat ve dvou krocích. Nejdřív je nutné definovat dvojici název/knihovna DLL. Když pak použijete **idl_module** k určení vstupního bodu, zadejte název a další atributy.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak použít atribut **idl_module** :

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Jakékoli|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[entry](entry.md)