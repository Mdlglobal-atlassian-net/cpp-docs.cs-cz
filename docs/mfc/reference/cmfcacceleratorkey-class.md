---
title: Cmfcacceleratorkey – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d87b7a2a76ea73989a9ab7dd845666625e91aa0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711591"
---
# <a name="cmfcacceleratorkey-class"></a>Cmfcacceleratorkey – třída
Pomocná třída, která implementuje virtuální mapování kláves a formátování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Vytvoří `CMFCAcceleratorKey` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCAcceleratorKey::Format](#format)|Přeloží AKCELERACE struktury na jeho vizuální reprezentace.|  
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Nastaví klávesovou zkratku `CMFCAcceleratorKey` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Klávesy akcelerátoru jsou také známé jako klávesové zkratky. Pokud chcete zobrazit klávesové zkratky, které uživatel zadá, [cmfcacceleratorkeyassignctrl – třída](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) mapy klávesové zkratky, jako je například Alt + Shift + S, na vlastní textovém formátu, jako je například "Alt + Shift + S". Každý `CMFCAcceleratorKey` objektu se mapuje na formátu textu s jednoklávesovou zkratkou.  
  
 Další informace o tom, jak používat klávesové zkratky a tabulek akcelerátorů najdete v tématu [ckeyboardmanager – třída](../../mfc/reference/ckeyboardmanager-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCAcceleratorKey` objekt a jak používat jeho `Format` metoda.  
  
 [!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAcceleratorKey`   
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxacceleratorkey.h  
  
##  <a name="cmfcacceleratorkey"></a>  CMFCAcceleratorKey::CMFCAcceleratorKey  
 Vytvoří [cmfcacceleratorkey –](../../mfc/reference/cmfcacceleratorkey-class.md) objektu.  
  
```  
CMFCAcceleratorKey();  
CMFCAcceleratorKey(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parametry  
*lpAccel*<br/>
[in] Ukazatel na klávesovou zkratku.  
  
### <a name="remarks"></a>Poznámky  
 Pokud nezadáte klávesovou zkratku při vytváření `CMFCAccleratorKey`, použijte [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) metoda, jak přidružit klávesovou zkratku s vaší `CMFCAcceleratorKey` objektu.  
  
##  <a name="format"></a>  CMFCAcceleratorKey::Format  
 Přeloží AKCELERACE struktura jeho přidružené řetězcovou hodnotu.  
  
```  
void Format(CString& str) const;  
```  
  
### <a name="parameters"></a>Parametry  
*str*<br/>
[out] Odkaz na `CString` objektu, ve kterém Metoda zapíše přeložené klávesovou zkratku.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda načte řetězec formátu přidružené klávesovou zkratku. Můžete nastavit formát řetězce [cmfcacceleratorkey –](../../mfc/reference/cmfcacceleratorkey-class.md) pomocí konstruktoru nebo metody [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).  
  
##  <a name="setaccelerator"></a>  CMFCAcceleratorKey::SetAccelerator  
 Nastaví klávesovou zkratku [cmfcacceleratorkey –](../../mfc/reference/cmfcacceleratorkey-class.md) objektu.  
  
```  
void SetAccelerator(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parametry  
*lpAccel*<br/>
[in] Ukazatel na klávesovou zkratku.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k nastavení klávesovou zkratku `CMFCAcceleratorKey` Pokud jste neposkytl klávesovou zkratku při vytváření `CMFCAcceleratorKey`.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager – třída](../../mfc/reference/ckeyboardmanager-class.md)
