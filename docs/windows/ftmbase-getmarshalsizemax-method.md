---
title: Ftmbase::getmarshalsizemax – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
dev_langs:
- C++
helpviewer_keywords:
- GetMarshalSizeMax method
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c7976d0ea22a0bf6f59b020f892d407c4721b9a7
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652354"
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax – metoda
Získejte horní mez počtu bajtů potřebných k zařazování zadaný ukazatel rozhraní na zadaný objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHODIMP GetMarshalSizeMax(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out DWORD *pSize  
) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *riid*  
 Odkaz na identifikátor rozhraní zařadit.  
  
 *PV*  
 Ukazatel rozhraní na zařadit; může mít hodnotu NULL.  
  
 *dwDestContext*  
 Cílový kontext, kde má být sdružení daného rozhraní.  
  
 Zadejte jednu nebo více hodnot výčtu MSHCTX.  
  
 V současné době unmarshaling situace může nastat v jiném objektu apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu ve stejném počítači jako aktuální proces (MSHCTX_LOCAL).  
  
 *pvDestContext*  
 Vyhrazeno pro budoucí použití; musí mít hodnotu NULL.  
  
 *mshlflags*  
 Příznak označující, zda je data, která mají být zařazen do dají přenést zpátky do klienta procesu – typické případy – nebo zapisují do globální tabulky, kde se dá načíst pomocí více klientů. Zadejte jednu nebo více hodnot výčtu MSHLFLAGS.  
  
 *pSize*  
 Když tato operace dokončena, ukazatel na horní mez na množství dat k zápisu do streamu zařazování.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; nebo jinak E_NOINTERFACE E_FAIL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [FtmBase – třída](../windows/ftmbase-class.md)