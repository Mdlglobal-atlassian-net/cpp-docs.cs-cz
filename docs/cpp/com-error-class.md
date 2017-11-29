---
title: "_com_error – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error
dev_langs: C++
helpviewer_keywords: _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1cb40690770094582eee87294d250d16d22b9c0c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="comerror-class"></a>_com_error – třída
**Konkrétní Microsoft**  
  
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
|[ErrorInfo –](../cpp/com-error-errorinfo.md)|Načte `IErrorInfo` objekt předaný konstruktoru.|  
|[Wcode –](../cpp/com-error-wcode.md)|Načte kód chyby 16bitové namapovat na zapouzdřené `HRESULT`.|  
  
### <a name="ierrorinfo-functions"></a>Funkce IErrorInfo  
  
|||  
|-|-|  
|[Popis](../cpp/com-error-description.md)|Volání `IErrorInfo::GetDescription` funkce.|  
|[HelpContext –](../cpp/com-error-helpcontext.md)|Volání `IErrorInfo::GetHelpContext` funkce.|  
|[Soubor nápovědy](../cpp/com-error-helpfile.md)|Volání `IErrorInfo::GetHelpFile` – funkce|  
|[Zdroj](../cpp/com-error-source.md)|Volání `IErrorInfo::GetSource` funkce.|  
|[IDENTIFIKÁTOR GUID](../cpp/com-error-guid.md)|Volání `IErrorInfo::GetGUID` funkce.|  
  
### <a name="format-message-extractor"></a>Formát zprávy Extraktor  
  
|||  
|-|-|  
|[Chybová zpráva](../cpp/com-error-errormessage.md)|Načte zprávu řetězec pro HRESULT uložené v `_com_error` objektu.|  
  
### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode k HRESULT Mappers  
  
|||  
|-|-|  
|[Hresulttowcode –](../cpp/com-error-hresulttowcode.md)|Mapuje 32-bit `HRESULT` na 16bitové `wCode`.|  
|[Wcodetohresult –](../cpp/com-error-wcodetohresult.md)|Mapuje 16bitové `wCode` na 32-bit `HRESULT`.|  
  
**Konkrétní Microsoft END**  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** comdef.h  
  
 `Lib:`comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) informace)  
  
## <a name="see-also"></a>Viz také  
 [Třídy podpory modelu comp kompilátoru](../cpp/compiler-com-support-classes.md)   
 [IErrorInfo rozhraní](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)