---
title: Třída CDebugReportHook | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d84b2da8a347833513e0725695bb9d2bacd2951d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cdebugreporthook-class"></a>CDebugReportHook – třída
Tato třída slouží k ladění sestavy poslat pojmenovaný kanál.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CDebugReportHook
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Volání [SetPipeName](#setpipename), [SetTimeout](#settimeout), a [SetHook](#sethook).|  
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|Volání [CDebugReportHook::RemoveHook](#removehook).|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Statické) Vlastní funkce vytváření sestav, která je byl zapojen do běhu C ladění procesu generování sestav.|  
|[CDebugReportHook::RemoveHook](#removehook)|Voláním této metody lze zastavit odesílání sestav ladění k pojmenovanému kanálu a obnovit předchozí háku sestavy.|  
|[CDebugReportHook::SetHook](#sethook)|Voláním této metody lze zahájit odesílání sestav ladění k pojmenovanému kanálu.|  
|[CDebugReportHook::SetPipeName](#setpipename)|Volejte tuto metodu a nastavit počítač a název kanálu, na které se budou odesílat sestavy ladění.|  
|[CDebugReportHook::SetTimeout](#settimeout)|Volejte tuto metodu a nastavit čas v milisekundách, že tato třída počká na pojmenovaný kanál k dispozici.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvoření instance této třídy v sestavení pro ladění služeb nebo aplikací na odesílat sestavy ladění pojmenovaný kanál. Ladění sestavy jsou generovány při volání [_crtdbgreport –](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) nebo pomocí obálku pro tuto funkci, jako [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) a [ATLASSERT](debugging-and-error-reporting-macros.md#atlassert) makra.  
  
 Pomocí této třídy můžete interaktivně ladění součásti spuštěné v neinteraktivním [okno stanice](http://msdn.microsoft.com/library/windows/desktop/ms687096).  
  
 Všimněte si, že se odesílají zprávy ladění pomocí základního kontextu zabezpečení vlákna. Zosobnění je dočasně zakázána, aby ladění sestavy můžete zobrazit v situacích, kde zosobnění uživatelů s nízkým oprávněním probíhající, například ve webových aplikacích.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  
  
##  <a name="cdebugreporthook"></a>  CDebugReportHook::CDebugReportHook  
 Volání [SetPipeName](#setpipename), [SetTimeout](#settimeout), a [SetHook](#sethook).  
  
```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `szMachineName`  
 Název počítače, které se mají posílat výstup ladění. Výchozí hodnota je v místním počítači.  
  
 `szPipeName`  
 Název pojmenovaného kanálu, které se mají posílat výstup ladění.  
  
 `dwTimeout`  
 Doba v milisekundách, že tato třída počká na pojmenovaný kanál k dispozici.  
  
##  <a name="dtor"></a>  CDebugReportHook:: ~ CDebugReportHook  
 Volání [CDebugReportHook::RemoveHook](#removehook).  
  
```
~CDebugReportHook() throw();
```  
  
##  <a name="cdebugreporthookproc"></a>  CDebugReportHook::CDebugReportHookProc  
 Vlastní funkce vytváření sestav, která je byl zapojen do běhu C ladění procesu generování sestav.  
  
```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `reportType`  
 Typ sestavy (_CRT_WARN, _CRT_ERROR nebo _CRT_ASSERT).  
  
 `message`  
 Řetězec zprávy.  
  
 *ReturnValue*  
 Hodnota, která má být vrácen podle [_crtdbgreport –](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu FALSE, pokud hák zpracovává zprávy v úplně tak, aby další vykazování se nevyžaduje. Vrátí hodnotu TRUE, pokud `_CrtDbgReport` by měl sestavy zprávu obvyklým způsobem.  
  
### <a name="remarks"></a>Poznámky  
 Funkci generování sestav se pokusí otevřít pojmenovaný kanál a komunikaci s procesem na druhém konci. Pokud kanál je zaneprázdněný, generování sestav funkce počká kanálu je zdarma nebo vyprší časový limit. Časový limit může být nastavena v konstruktoru nebo volání [CDebugReportHook::SetTimeout](#settimeout).  
  
 Kód v této funkci se spustí v kontextu zabezpečení základní volající vlákno, to znamená, že je zakázána zosobnění dobu trvání této funkce.  
  
##  <a name="removehook"></a>  CDebugReportHook::RemoveHook  
 Voláním této metody lze zastavit odesílání sestav ladění k pojmenovanému kanálu a obnovit předchozí háku sestavy.  
  
```
void RemoveHook() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání [_crtsetreporthook2 –](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) obnovit předchozí háku sestavy.  
  
##  <a name="sethook"></a>  CDebugReportHook::SetHook  
 Voláním této metody lze zahájit odesílání sestav ladění k pojmenovanému kanálu.  
  
```
void SetHook() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání [_crtsetreporthook2 –](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) tak, aby měl ladění sestavy směrován přes [CDebugReportHookProc](#cdebugreporthookproc) k pojmenovanému kanálu. Tato třída uchovává informace o předchozích háku sestavy tak, aby je bylo možné obnovit při [RemoveHook](#removehook) je volána.  
  
##  <a name="setpipename"></a>  CDebugReportHook::SetPipeName  
 Volejte tuto metodu a nastavit počítač a název kanálu, na které se budou odesílat sestavy ladění.  
  
```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```  
  
### <a name="parameters"></a>Parametry  
 `szMachineName`  
 Název počítače, které se mají posílat výstup ladění.  
  
 `szPipeName`  
 Název pojmenovaného kanálu, které se mají posílat výstup ladění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
##  <a name="settimeout"></a>  CDebugReportHook::SetTimeout  
 Volejte tuto metodu a nastavit čas v milisekundách, že tato třída počká na pojmenovaný kanál k dispozici.  
  
```
void SetTimeout(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>Parametry  
 `dwTimeout`  
 Doba v milisekundách, že tato třída počká na pojmenovaný kanál k dispozici.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../atl/reference/atl-classes.md)
