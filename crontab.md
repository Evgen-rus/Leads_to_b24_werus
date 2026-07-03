5. Настроить расписание cron (MSK), добавить в `crontab -e`:
   ```bash
   crontab -e
   ```
   
   ```
   # ==== Leads_to_b24_werus SCHEDULE ====
   CRON_TZ=Europe/Moscow
   33 8-17 * * * cd /opt/Leads_to_b24_werus && /opt/Leads_to_b24_werus/venv/bin/python 1_save_gsheet_to_sqlite.py >/dev/null 2>> /opt/Leads_to_b24_werus/logs/cron_save_gsheet.log
   35 8-17 * * * cd /opt/Leads_to_b24_werus && /opt/Leads_to_b24_werus/venv/bin/python 2_upload_sqlite_to_bitrix.py >/dev/null 2>> /opt/Leads_to_b24_werus/logs/cron_upload_sqlite.log
   ```

   После проверки cron можно отключить отдельные cron-логи:

```cron
# ==== Leads_to_b24_werus SCHEDULE ====
CRON_TZ=Europe/Moscow
33 8-17 * * * cd /opt/Leads_to_b24_werus && /opt/Leads_to_b24_werus/venv/bin/python 1_save_gsheet_to_sqlite.py >/dev/null 2>/dev/null
35 8-17 * * * cd /opt/Leads_to_b24_werus && /opt/Leads_to_b24_werus/venv/bin/python 2_upload_sqlite_to_bitrix.py >/dev/null 2>/dev/null