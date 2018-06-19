---
title: Třída CSimpleException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d04a2f643add489d3302e58a9bde995303ecddd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369922"
---
# <a name="csimpleexception-class"></a>CSimpleException – třída
Tato třída je základní třídu pro kritické prostředků MFC – výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AFX_NOVTABLE CSimpleException : public CException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleException::CSimpleException](#csimpleexception)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleException::GetErrorMessage](#geterrormessage)|Poskytuje text o chybu, ke které došlo k chybě.|  
  
## <a name="remarks"></a>Poznámky  
 `CSimpleException` Základní třída pro prostředek kritické výjimky MFC a zpracovává vlastnictví a inicializace chybovou zprávu. Následující třídy použití `CSimpleException` jako jejich základní třídy:  
  
|||  
|-|-|  
|[CMemoryException – třída](../../mfc/reference/cmemoryexception-class.md)|Výjimky nedostatku paměti|  
|[CNotSupportedException – třída](../../mfc/reference/cnotsupportedexception-class.md)|Žádosti o nepodporovanou operaci|  
|[CResourceException – třída](../../mfc/reference/cresourceexception-class.md)|Windows prostředek nebyl nalezen nebo není vytvořitelné|  
|[CUserException – třída](../../mfc/reference/cuserexception-class.md)|Výjimka, která určuje prostředek nebyl nalezen.|  
|[CInvalidArgException – třída](../../mfc/reference/cinvalidargexception-class.md)|Výjimka, která určuje neplatný argument.|  
  
 Protože `CSimpleException` je abstraktní základní třídu, nelze deklarovat `CSimpleException` objektu přímo. Místo toho je potřeba deklarovat odvozené objekty jsou v předchozí tabulce. Pokud jsou deklarace vlastní odvozené třídy, použijte jako model předchozí třídy.  
  
 Další informace najdete v tématu [CException – třída](../../mfc/reference/cexception-class.md) tématu a [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CSimpleException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="csimpleexception"></a>  CSimpleException::CSimpleException  
 Konstruktor  
  
```  
CSimpleException();  
explicit CSimpleException(BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parametry  
 `bAutoDelete`  
 Zadejte **TRUE** Pokud paměti pro `CSimpleException` objekt byl přidělen v haldě. To způsobí, že `CSimpleException` objekt, který chcete odstranit, když **odstranit** – členská funkce je volána odstranit výjimku. Zadejte **FALSE** Pokud `CSimpleException` objekt je v zásobníku nebo je objekt globální. V takovém případě `CSimpleException` objekt nebude odstraněn, když **odstranit** členské funkce je volána.  
  
### <a name="remarks"></a>Poznámky  
 Potřebovali byste normálně nikdy přímo volat tento konstruktor. Funkci, která vyvolá výjimku, by měl vytvořit instanci `CException`-odvozené třídy a volat jeho konstruktoru, nebo pomocí některé z knihovny MFC vyvoláním funkce, jako například [afxthrowfileexception –](exception-processing.md#afxthrowfileexception), má být vyvolána předdefinované typu.  
  
##  <a name="geterrormessage"></a>  CSimpleException::GetErrorMessage  
 Volání této funkce člen zajistit text o chybu, ke které došlo k chybě.  
  
```  
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszError`  
 Ukazatel na vyrovnávací paměť, která se zobrazí chybová zpráva.  
  
 `nMaxError`  
 Maximální počet znaků, vyrovnávací paměť, mohou být uloženy včetně **NULL** ukončovací znak.  
  
 `pnHelpContext`  
 Adresa **Celé_číslo** , obdrží ID kontextové nápovědy Pokud **NULL**, bude vrácen žádné ID.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0, pokud žádná chybová zpráva textu je k dispozici.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CException – třída](../../mfc/reference/cexception-class.md)   
 [Zpracování výjimek](../../mfc/exception-handling-in-mfc.md)



