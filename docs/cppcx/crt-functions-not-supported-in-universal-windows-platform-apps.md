---
title: "CRT – funkce není podporována v aplikacích pro univerzální platformu Windows | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 65d058780ee71731559733ac07eef3f614a47784
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>CRT – funkce není podporována v aplikacích pro univerzální platformu Windows
Mnoho funkcí jazyka C runtime (CRT) nejsou k dispozici, při sestavování aplikací pro univerzální platformu Windows (UWP). V některých případech jsou k dispozici alternativní řešení – – například můžete použít rozhraní API Win32 nebo prostředí Windows Runtime. Ale v ostatních případech funkcí CRT zakázali protože funkce, které odpovídají jejich nebo podporující rozhraní API neplatí pro aplikace UWP.  
  
 Následující tabulka uvádí funkce CRT, které nejsou k dispozici při sestavování aplikací UWP a označuje žádné alternativní řešení, které se vztahují.  
  
## <a name="unsupported-crt-functions"></a>Nepodporované CRT – funkce  
  
||||  
|-|-|-|  
|_beep _sleep _seterrormode|Tyto funkce byly v předchozích verzích CRT zastaralé. Kromě toho nejsou k dispozici pro aplikace UWP odpovídající rozhraní API Win32.|Alternativní řešení neexistuje.|  
|getcwd – _chdrive – chdir –|Tyto funkce jsou zastaralé nebo nejsou bezpečné pro přístup z více vláken.|_Chdir – použití _getcwd – a souvisejících funkcí.|  
|_cgets – _cgets_s – _cgetws – _cgetws_s – _cprintf – _cprintf_l – _cprintf_p – _cprintf_p_l – _cprintf_s – _cprintf_s_l – _cputs – _cputws – _cscanf – _cscanf_l – _cscanf_s – _cscanf_s_l – _cwait – _cwprintf – _cwprintf_l – _cwprintf_p – _cwprintf_p_l – _cwprintf_s – _cwprintf_s_l – _cwscanf – _ cwscanf_l – _cwscanf_s – _cwscanf_s_l – _vcprintf – _vcprintf_l – _vcprintf_p – _vcprintf_p_l – _vcprintf_s – _vcprintf_s_l – _vcwprintf – _vcwprintf_l – _vcwprintf_p – _vcwprintf_p_l – _vcwprintf_s – _vcwprintf_s_l – _getch – _getch_nolock – _getche – _getche_nolock – _getwch – _ getwch_nolock – _getwche – _getwche_nolock – _putch – _putch_nolock – _putwch – _putwch_nolock – _ungetch – _ungetch_nolock – _ungetwch – _ungetwch_nolock – _kbhit – kbhit – putch – cgets – cprintf – cputs – cscanf – cwait – getch – getche – ungetch –|Tyto funkce slouží ke čtení a zápisu přímo z a do konzoly. Aplikace UWP jsou pouze; grafického uživatelského rozhraní nepodporují konzoly.|Alternativní řešení neexistuje.|  
|getpid|Tato funkce je zastaralé.|Použít _getpid – nebo rozhraní API Win32 `GetCurrentProcessId()`.|  
|_getdiskfree|Není k dispozici.|Použít rozhraní API Win32 `GetDiskFreeSpaceExW()`.|  
|_getdrives – _getdrive –|Odpovídající rozhraní API není k dispozici pro aplikace UWP.|Alternativní řešení neexistuje.|  
|_inp – _inpd – _inpw – _outp – _outpd – _outpw – INP – inpd – inpw – outp – outpd – outpw –|Port vstupně-výstupní operace není podporována v aplikacích pro UPW.|Alternativní řešení neexistuje.|  
|_ismbcalnum – _ismbcalnum_l – _ismbcalpha – _ismbcalpha_l – _ismbcdigit – _ismbcdigit_l – _ismbcgraph – _ismbcgraph_l – _ismbchira – _ismbchira_l – _ismbckata – _ismbckata_l – _ismbcl0 – _ismbcl0_l – _ismbcl1 – _ismbcl1_l – _ismbcl2 – _ismbcl2_l – _ismbclegal – _ismbclegal_l – _ ismbclower – _ismbclower_l – _ismbcprint – _ismbcprint_l – _ismbcpunct – _ismbcpunct_l – _ismbcspace – _ismbcspace_l – _ismbcsymbol – _ismbcsymbol_l – _ismbcupper – _ismbcupper_l – _mbbtombc – _mbbtombc_l – _mbbtype – _mbbtype_l – _mbccpy – _mbccpy_l – _mbccpy_s – _mbccpy_s_l – _ mbcjistojms – _mbcjistojms_l – _mbcjmstojis – _mbcjmstojis_l – _mbclen _mbclen_l _mbctohira – _mbctohira_l – _mbctokata – _mbctokata_l – _mbctolower – _mbctolower_l – _mbctombb – _mbctombb_l – _mbctoupper – _mbctoupper_l – _mbsbtype – _mbsbtype_l – _mbscat – _mbscat_l _mbscat_s – _ mbscat_s_l _mbschr – _mbschr_l – _mbscmp – _mbscmp_l _mbscoll – _mbscoll_l _mbscpy – _mbscpy_l _mbscpy_s – _mbscpy_s_l _mbscspn – _mbscspn_l – _mbsdec _mbsdec_l – _mbsicmp – _mbsicmp_l – _mbsicoll – _mbsicoll_l – _mbsinc _mbsinc_l – _mbslen – _mbslen_l – _mbslwr – _mbslwr_l – _mbslwr_s – _mbslwr_s_l – _mbsnbcat – _mbsnbcat_l – _mbsnbcat_s – _mbsnbcat_s_l – _mbsnbcmp – _mbsnbcmp_l – _mbsnbcnt – _mbsnbcnt_l – _mbsnbcoll – _mbsnbcoll_l – _mbsnbcpy – _mbsnbcpy_l – _mbsnbcpy_s – _mbsnbcpy_s_l – _mbsnbicmp – _mbsnbicmp_l – _mbsnbicoll – _mbsnbicoll_l – _mbsnbset – _mbsnbset – _l _mbsnbset_s – _mbsnbset_s_l – _mbsncat – _mbsncat_l – _mbsncat_s – _mbsncat_s_l – _mbsnccnt – _mbsnccnt_l – _mbsncmp – _mbsncmp_l – _mbsncoll – _mbsncoll_l – _mbsncpy – _mbsncpy_l – _mbsncpy_s _mbsncpy_s_l _mbsnextc – _mbsnextc_l – _mbsnicmp – _mbsnicmp_l – _mbsnicoll – _mbsnicoll_ l _mbsninc – _mbsninc_l – _mbsnlen – _mbsnlen_l – _mbsnset – _mbsnset_l – _mbsnset_s – _mbsnset_s_l – _mbspbrk – _mbspbrk_l – _mbsrchr – _mbsrchr_l – _mbsrev _mbsrev_l – _mbsset – _mbsset_l – _mbsset_s – _mbsset_s_l – _mbsspn – _mbsspn_l – _mbsspnp – _mbsspnp_l – _mbsstr – _mbsstr_l – _mbstok – _ mbstok_l – _mbstok_s – _mbstok_s_l – _mbsupr – _mbsupr_l – _mbsupr_s – _mbsupr_s_l – is_wctype|Vícebajtové řetězce nejsou podporovány v aplikacích pro UPW.|Místo toho použijte řetězců v kódu Unicode.|  
|_pclose – _pipe – _popen – _wpopen –|Funkce kanálu není k dispozici pro aplikace UWP.|Alternativní řešení neexistuje.|  
|_resetstkoflw|Podporující rozhraní API Win32 nejsou k dispozici pro aplikace UWP.|Alternativní řešení neexistuje.|  
|_getsystime _setsystime|Tyto byly zastaralé rozhraní API v předchozích verzích CRT. Navíc nelze uživatel nastavit systémového času v aplikaci UWP z důvodu nedostatku oprávnění.|Pouze systémového času, použijte rozhraní API Win32 `GetSystemTime`. Systémový čas nelze nastavit.|  
|_environ – _putenv – _putenv_s – _searchenv – _searchenv_s – _dupenv_s – _wputenv – _wputenv_s – _wsearchenv – GETENV – getenv_s – putenv – _wdupenv_s – _wenviron – _wgetenv – _wgetenv_s – _wsearchenv_s – tzset –|Nejsou k dispozici pro aplikace UWP proměnné prostředí.|Alternativní řešení neexistuje. Pokud chcete nastavit časové pásmo, použijte _tzset –.|  
|_loaddll _getdllprocaddr _unloaddll|Tyto byly zastaralé funkce v předchozích verzích CRT. Navíc uživatele nelze načíst knihovny DLL s výjimkou od funkcí ve stejném balíčku aplikace.|Použít rozhraní API Win32 `LoadPackagedLibrary`, `GetProcAddress`, a `FreeLibrary` načtení a použití zabalené knihovny DLL.|  
|_wexecl – _wexecle – _wexeclp – _wexeclpe – _wexecv – _wexecve – _wexecvp – _wexecvpe – _execl – _execle – _execlp – _execlpe – _execv – _execve – _execvp – _execvpe – _spawnl – _spawnle – _spawnlp – _spawnlpe – _spawnv – _spawnve – _spawnvp – _spawnvpe – _wspawnl – _wspawnle – _wspawnlp – _wspawnlpe – _ wspawnv – _wspawnve – _wspawnvp – _wspawnvpe – _wsystem – execl – execle – execlp – execlpe – execv – execve – execvp – execvpe – spawnl – spawnle – spawnlp – spawnlpe – spawnv – spawnve – spawnvp – spawnvpe – systém|Funkce není k dispozici v aplikacích pro UPW. Aplikace pro UPW nelze vyvolat v jiné aplikaci UWP nebo aplikace na ploše.|Alternativní řešení neexistuje.|  
|_heapwalk – _heapadd – _heapchk – _heapset – _heapused|Tyto funkce jsou obvykle používány pro práci s haldě. Odpovídající rozhraní API Win32 však nejsou podporovány v aplikacích pro UPW. A aplikace už můžete vytvořit nebo použít privátní haldách.|Alternativní řešení neexistuje. Ale `_heapwalk` k dispozici v ladění CRT pouze pro účely ladění. Tyto nelze použít v aplikacích, které jsou odeslány na web Windows Store.|  
  
 Následující funkce jsou k dispozici v CRT pro aplikace UWP, ale měli použít pouze v případě, že odpovídající Win32 nebo rozhraní API systému Windows Runtime nelze použít – například když provádíte přenos rozsáhlých základů kódu  
  
|||  
|-|-|  
|Funkce řetězce jednobajtové – například `strcat`, `strcpy`, `strlwr`a tak dále.|Zkontrolujte aplikace UWP výhradně kódování Unicode vzhledem k tomu, že všechna rozhraní API Win32 a modul Runtime rozhraní API systému Windows, které jsou zveřejněné pomocí znakové sady pouze kódování Unicode.  Funkce jednobajtové byly ponechány pro velké kód – portování základny, ale jinak by se mělo zabránit, a odpovídající funkce široké char by místo toho použít, pokud je to možné.|  
|Stream vstupně-výstupní operace a funkce vstupně-výstupní operace nízké úrovně souboru – například `fopen`, `open`a tak dále.|Tyto funkce jsou synchronní, které se nedoporučuje pro aplikace UWP. V aplikacích pro UPW pomocí rozhraní API pro asynchronní otevřít, číst z a zápis do souborů, aby se zabránilo uzamykání vlákna uživatelského rozhraní. Příkladem takových rozhraní API jsou v `Windows::Storage::FileIO` třídy.|  
  
## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Aplikace pro Windows 8.x Store a Windows Phone 8.x aplikace  
 Kromě výše uvedených rozhraní API nejsou k dispozici v aplikacích pro Windows 8.x Store a Windows Phone 8.x aplikace následující rozhraní API.  
  
||||  
|-|-|-|  
|_beginthread – _beginthreadex _endthread _endthreadex|Vláken rozhraní API Win32 nejsou k dispozici v aplikacích pro Windows 8.x Store.|Použití `Windows Runtime Windows::System::Threading::ThreadPool` nebo `concurrency::task` místo.|  
|_chdir – _wchdir – _getcwd – _getdcwd – _wgetdcwd – _wgetcwd –|Koncept pracovního adresáře neplatí pro aplikace pro Windows 8.x Store.|Místo toho použijte úplné cesty.|  
|_getpid|Tato funkce se v předchozích verzích CRT zastaralé.|Použít rozhraní API Win32`GetCurrentProcessId()`|  
|_ismbbalnum – _isleadbyte_l –, _ismbbalnum_l –, _ismbbalpha –, _ismbbalpha – _ismbbalpha_l – _ismbbgraph – _ismbbgraph_l – _ismbbkalnum – _ismbbkalnum_l – _ismbbkana – _ismbbkana_l – _ismbbkprint – _ismbbkprint_l – _ismbbkpunct – _ismbbkpunct_l – _ismbblead – _ismbblead_l – _ ismbbprint – _ismbbprint_l – _ismbbpunct – _ismbbpunct_l – _ismbbtrail – _ismbbtrail_l – _ismbslead – _ismbslead_l – _ismbstrail – _ismbstrail_l – _mbsdup – isleadbyte –|Vícebajtové řetězce nejsou podporovány v aplikacích pro Windows 8.x Store.|Místo toho použijte řetězců v kódu Unicode.|  
|_tzset|Proměnné prostředí nejsou k dispozici pro aplikace pro Windows 8.x Store.|Alternativní řešení neexistuje.|  
|_get_heap_handle –, _heapmin –|Odpovídající rozhraní API Win32 nejsou podporovány v aplikacích pro Windows 8.x Store. A aplikace už nemůžete vytvářet privátní haldách.|Alternativní řešení neexistuje. Ale `_get_heap_handle` je k dispozici v ladění CRT pouze pro účely ladění.|