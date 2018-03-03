---
title: "_com_error – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53defbe6c686630791317fa20aca48414144eb91
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="comerror-class"></a>_com_error – třída
**Microsoft Specific**  
  
 A `_com_error` objekt představuje podmínku vyhledat pomocí funkce obálky zpracování chyb v souborech hlavičky generované z knihovny typů nebo jednu z tříd COM podpory. `_com_error` Třída zapouzdří `HRESULT` kód chyby a všechny přidružené `IErrorInfo Interface` objektu.  
  
### <a name="construction"></a>Konstrukce  
  
|||  
|-|-|  
|[_com_error](../cpp/com-error-com-error.md)|Vytvoří `_com_error` objektu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](../cpp/com-error-operator-equal.md)|Přiřadí existující `_com_error` objekt do jiné.|  
  
### <a name="extractor-functions"></a>Extraktor funkce  
  
|||  
|-|-|  
|[Chyba](../cpp/com-error-error.md)|Načte `HRESULT` předaný konstruktoru.|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Načte `IErrorInfo` objekt předaný konstruktoru.|  
|[WCode](../cpp/com-error-wcode.md)|Načte kód chyby 16bitové namapovat na zapouzdřené `HRESULT`.|  
  
### <a name="ierrorinfo-functions"></a>Funkce IErrorInfo  
  
|||  
|-|-|  
|[Popis](../cpp/com-error-description.md)|Volání `IErrorInfo::GetDescription` funkce.|  
|[HelpContext](../cpp/com-error-helpcontext.md)|Volání `IErrorInfo::GetHelpContext` funkce.|  
|[Soubor nápovědy](../cpp/com-error-helpfile.md)|Volání `IErrorInfo::GetHelpFile` – funkce|  
|[Zdroj](../cpp/com-error-source.md)|Volání `IErrorInfo::GetSource` funkce.|  
|[GUID](../cpp/com-error-guid.md)|Volání `IErrorInfo::GetGUID` funkce.|  
  
### <a name="format-message-extractor"></a>Formát zprávy Extraktor  
  
|||  
|-|-|  
|[Chybová zpráva](../cpp/com-error-errormessage.md)|Načte zprávu řetězec pro HRESULT uložené v `_com_error` objektu.|  
  
### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode k HRESULT Mappers  
  
|||  
|-|-|  
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Mapuje 32-bit `HRESULT` na 16bitové `wCode`.|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapuje 16bitové `wCode` na 32-bit `HRESULT`.|  
  
**Konkrétní Microsoft END**  
  
## <a name="requirements"></a>Požadavky  
 **Header:** \<comdef.h>  
  
 `Lib:`comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) informace)  
  
## <a name="see-also"></a>Viz také  
 [Třídy podpory modelu comp kompilátoru](../cpp/compiler-com-support-classes.md)   
 [IErrorInfo rozhraní](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)