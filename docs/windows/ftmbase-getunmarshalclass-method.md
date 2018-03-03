---
title: "Ftmbase::getunmarshalclass – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
dev_langs:
- C++
helpviewer_keywords:
- GetUnmarshalClass method
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 978379c64f22026f19dd76afa39af08402cebc65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass – metoda
Získá CLSID, který COM používá k nalezení DLL obsahující kód pro odpovídající proxy server. COM načte tuto knihovnu DLL k vytvoření instance Neinicializovaný proxy serveru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Odkaz na identifikátor rozhraní být zařazena.  
  
 `pv`  
 Ukazatel rozhraní zařazována; může mít hodnotu NULL, pokud má volající nemá požadované rozhraní ukazatel.  
  
 `dwDestContext`  
 Cílový kontext, kde má být zařazeny specifikované rozhraní.  
  
 Zadejte jeden nebo více hodnot výčtu MSHCTX.  
  
 Unmarshaling situace může nastat v jiném objektu apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu na stejném počítači jako aktuální proces (MSHCTX_LOCAL).  
  
 `pvDestContext`  
 Vyhrazeno pro budoucí použití; musí mít hodnotu NULL.  
  
 `mshlflags`  
 Když tato operace dokončí, ukazatel na CLSID, který se má použít k vytvoření proxy serveru v procesu klienta.  
  
 `pCid`  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném S_FALSE.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [FtmBase – třída](../windows/ftmbase-class.md)