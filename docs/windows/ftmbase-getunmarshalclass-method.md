---
title: Ftmbase::getunmarshalclass – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
dev_langs:
- C++
helpviewer_keywords:
- GetUnmarshalClass method
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 167ad8537a11a0118c15b588b353f33775b5ab3a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644996"
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass – metoda
Získá identifikátor CLSID, který COM používá k nalezení knihovny DLL obsahující kód pro odpovídající server proxy. COM načte tuto knihovnu DLL vytvořit neinicializované instance serveru proxy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *riid*  
 Odkaz na identifikátor rozhraní zařadit.  
  
 *PV*  
 Ukazatel rozhraní k zařadit; může mít hodnotu NULL, pokud volající nemá ukazatel na požadované rozhraní.  
  
 *dwDestContext*  
 Cílový kontext, kde má být sdružení daného rozhraní.  
  
 Zadejte jednu nebo více hodnot výčtu MSHCTX.  
  
 Unmarshaling situace může nastat v jiném objektu apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu ve stejném počítači jako aktuální proces (MSHCTX_LOCAL).  
  
 *pvDestContext*  
 Vyhrazeno pro budoucí použití; musí mít hodnotu NULL.  
  
 *mshlflags*  
 Pokud tato operace dokončena, ukazatel na identifikátor CLSID se použije k vytvoření proxy serveru v procesu klienta.  
  
 *pCid*  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě S_FALSE.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [FtmBase – třída](../windows/ftmbase-class.md)