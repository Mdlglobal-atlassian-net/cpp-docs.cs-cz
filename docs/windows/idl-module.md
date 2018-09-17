---
title: možnost idl_module | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 73047962daf32eae6c01bb0ea6f6688a83e19402
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715530"
---
# <a name="idlmodule"></a>idl_module

Určuje vstupní bod v souboru .dll.

## <a name="syntax"></a>Syntaxe

```cpp
[ idl_module (
   name=module_name,
   dllname=dll,
   uuid="uuid",
   helpstring="help text",
   helpstringcontext=helpcontextID,
   helpcontext=helpcontext,
   hidden,
   restricted
) ]
function declaration
```

### <a name="parameters"></a>Parametry

*Jméno*  
Uživatelem definovaný název pro blok kódu, který se zobrazí v souboru IDL.

*NázevSouboru*  
(Volitelné) Soubor .dll, který obsahuje exportu.

*uuid*  
(Volitelné) Jedinečný identifikátor.

*helpstring*  
(Volitelné) Znakový řetězec používaný k popisu knihovny typů.

*helpstringcontext*  
(Volitelné) ID tématu nápovědy HLP nebo CHM souboru.

*helpcontext*  
(Volitelné) ID nápovědy pro tuto knihovnu typů.

*hidden*  
(Volitelné) Parametr, který zabraňuje zobrazení knihovny. Zobrazit [skryté](/windows/desktop/Midl/hidden) atribut MIDL pro další informace.

*restricted*  
(Volitelné) Členové knihovny nejde volat libovolně. Zobrazit [s omezeným přístupem](/windows/desktop/Midl/restricted) atribut MIDL pro další informace.

*deklarace funkce*  
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

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Samostatné atributy](../windows/stand-alone-attributes.md)  
[entry](../windows/entry.md)  