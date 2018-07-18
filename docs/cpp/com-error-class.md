---
title: _com_error – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d59782b62ddfb51601505be6d12f01ce14cd4f1
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026631"
---
# <a name="comerror-class"></a>_com_error – třída
**Specifické pro Microsoft**  
  
 A `_com_error` objekt představuje podmínku výjimky vyhledat pomocí funkce obálky zpracování chyb v souborech hlaviček generovaných z knihovny typů nebo jeden z třídy COM support. `_com_error` Třída zapouzdří kód chyby: HRESULT a všechny přidružené `IErrorInfo Interface` objektu.  
  
### <a name="construction"></a>Konstrukce  
  
|||  
|-|-|  
|[_com_error](../cpp/com-error-com-error.md)|Vytvoří `_com_error` objektu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](../cpp/com-error-operator-equal.md)|Přiřadí existující `_com_error` objektu na jiný.|  
  
### <a name="extractor-functions"></a>Extraktor funkcí  
  
|||  
|-|-|  
|[Chyba](../cpp/com-error-error.md)|Načte hodnotu HRESULT předaný konstruktoru.|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Načte `IErrorInfo` objekt předaný konstruktoru.|  
|[WCode](../cpp/com-error-wcode.md)|Načte 16bitové chybový kód namapovat na zapouzdřený HRESULT.|  
  
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
|[Chybová zpráva](../cpp/com-error-errormessage.md)|Získá řetězcovou zprávu pro HRESULT uložený ve `_com_error` objektu.|  
  
### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode k Mapovačů HRESULT  
  
|||  
|-|-|  
|[Hresulttowcode –](../cpp/com-error-hresulttowcode.md)|Mapuje 32-bit HRESULT na 16 bitů `wCode`.|  
|[Wcodetohresult –](../cpp/com-error-wcodetohresult.md)|Mapuje 16bitové `wCode` 32-bit HRESULT.|  
  
**Specifické pro END Microsoft**  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<comdef.h >  
  
 `Lib:` comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Další informace)  
  
## <a name="see-also"></a>Viz také  
 [Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)   
 [Rozhraní IErrorInfo](http://msdn.microsoft.com/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)