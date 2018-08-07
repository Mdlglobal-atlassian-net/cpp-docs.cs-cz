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
ms.openlocfilehash: bfda47ced14d7c112d27d0036b4d636e32c91907
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607557"
---
# <a name="idlmodule"></a>idl_module
Určuje vstupní bod v souboru .dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
 *NázevSouboru* (volitelné)  
 Soubor .dll, který obsahuje exportu.  
  
 *identifikátor UUID* (volitelné)  
 Jedinečný identifikátor.  
  
 *helpstring* (volitelné)  
 Znakový řetězec používaný k popisu knihovny typů.  
  
 *helpstringcontext –* (volitelné)  
 ID tématu nápovědy HLP nebo CHM souboru.  
  
 *HelpContext* (volitelné)  
 ID nápovědy pro tuto knihovnu typů.  
  
 *skryté* (volitelné)  
 Parametr, který zabraňuje zobrazení knihovny. Zobrazit [skryté](http://msdn.microsoft.com/library/windows/desktop/aa366861) atribut MIDL pro další informace.  
  
 *s omezeným přístupem* (volitelné)  
 Členové knihovny nejde volat libovolně. Zobrazit [s omezeným přístupem](http://msdn.microsoft.com/library/windows/desktop/aa367157) atribut MIDL pro další informace.  
  
 *deklarace funkce*  
 Funkce, která budou definovat.  
  
## <a name="remarks"></a>Poznámky  
 **Možnost idl_module** atribut C++ umožňuje zadat vstupní bod v souboru .dll, který umožňuje importovat ze souboru .dll.  
  
 **Možnost idl_module** atribut má podobné funkce [modulu](http://msdn.microsoft.com/library/windows/desktop/aa367099) atribut MIDL.  
  
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