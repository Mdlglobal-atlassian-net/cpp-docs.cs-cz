---
title: "idl_module – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.idl_module
dev_langs: C++
helpviewer_keywords: idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f052692686149b247a50c0d89e77797f4f48fab3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
  
#### <a name="parameters"></a>Parametry  
 **Jméno**  
 Uživatelem definovaný název bloku kódu, který se zobrazí v souboru.  
  
 **NázevSouboru** (volitelné)  
 Soubor .dll, který obsahuje exportu.  
  
 `uuid`(volitelné)  
 Jedinečný identifikátor.  
  
 **helpstring –** (volitelné)  
 Řetězec znaků používají k popisu knihovny typů.  
  
 **helpstringcontext –** (volitelné)  
 ID tématu nápovědy v souboru HLP nebo CHM.  
  
 **HelpContext –** (volitelné)  
 Pomůže ID pro tuto knihovnu typů.  
  
 **Skrytá** (volitelné)  
 Parametr, který zabraňuje zobrazení knihovny. Najdete v článku [Skrytá](http://msdn.microsoft.com/library/windows/desktop/aa366861) MIDL atribut pro další informace.  
  
 ***s omezeným přístupem*** (volitelné)  
 Členové knihovny nelze volat libovolně. Najdete v článku [s omezeným přístupem](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL atribut pro další informace.  
  
 *deklarace funkce*  
 Funkce, která určíte.  
  
## <a name="remarks"></a>Poznámky  
 `idl_module` C++ atribut umožňuje určit vstupní bod v souboru .dll, který umožňuje importovat ze souboru .dll.  
  
 **Idl_module –** atribut má podobné funkce [modulu](http://msdn.microsoft.com/library/windows/desktop/aa367099) MIDL atribut.  
  
 Můžete exportovat nic z objektu COM, který můžete exportovat ze souboru .dll umístěním vstupní bod knihovny DLL v bloku knihovny .idl souboru.  
  
 Vaše musí používat `idl_module` ve dvou krocích. Nejprve je nutné zadat dvojice název/DLL. Pak, když použijete `idl_module` k určení vstupního bodu, zadejte název a další atributy.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje způsob použití `idl_module` atribut:  
  
```  
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
|**Platí pro**|Odkudkoli|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
 [entry](../windows/entry.md)   
