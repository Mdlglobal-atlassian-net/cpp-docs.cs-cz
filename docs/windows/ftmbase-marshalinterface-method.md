---
title: Ftmbase::marshalinterface – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- MarshalInterface method
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23779cbe0b27680122c6aa3a8f8748c39f28078e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647404"
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface – metoda
Zapíše do datového proudu data potřebná k inicializaci objektu proxy v nějaký proces klienta.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHODIMP MarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags  
) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *pStm*  
 Ukazatel na datový proud, které se použijí při zařazování.  
  
 *riid*  
 Odkaz na identifikátor rozhraní zařadit. Toto rozhraní musí být odvozen od `IUnknown` rozhraní.  
  
 *PV*  
 Ukazatel na ukazatel rozhraní k zařadit; může mít hodnotu NULL, pokud volající nemá ukazatel na požadované rozhraní.  
  
 *dwDestContext*  
 Cílový kontext, kde má být sdružení daného rozhraní.  
  
 Zadejte jednu nebo více hodnot výčtu MSHCTX.  
  
 Unmarshaling situace může nastat v jiném objektu apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu ve stejném počítači jako aktuální proces (MSHCTX_LOCAL).  
  
 *pvDestContext*  
 Vyhrazeno pro budoucí použití; musí být nula.  
  
 *mshlflags*  
 Určuje, zda data, která mají být zařazen do dají přenést zpátky do klienta procesu – typické případy – nebo zapisují do globální tabulky, kde se dá načíst pomocí více klientů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěšně byl zařazen ukazatel rozhraní.  
  
 E_NOINTERFACE  
 Zadané rozhraní není podporováno.  
  
 STG_E_MEDIUMFULL  
 Datový proud je plná.  
  
 E_FAIL  
 Operace se nezdařila.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [FtmBase – třída](../windows/ftmbase-class.md)