    @Override
    public ApiResult likeVideo(String awemeId, int operationType) {
        try {
            String uifid = extractCookieField(cookies, "UIFID");
            if (uifid.isEmpty()) {
                String temp = extractCookieField(cookies, "UIFID_TEMP");
                if (!temp.isEmpty()) uifid = temp;
            }

            String url = "https://www-hj.douyin.com/aweme/v1/web/commit/item/digg/";
            Map<String,String> params = new LinkedHashMap<>();
            params.put("msToken", msToken);
            params.put("device_platform", "webapp");
            params.put("aid", "6383");
            params.put("channel", "channel_pc_web");
            params.put("pc_client_type", "1");
            params.put("pc_libra_divert", "Windows");
            params.put("update_version_code", "170400");
            params.put("support_h265", "1");
            params.put("support_dash", "1");
            params.put("version_code", "170400");
            params.put("version_name", "17.4.0");
            params.put("cookie_enabled", "true");
            params.put("screen_width", "2560");
            params.put("screen_height", "1440");
            params.put("browser_language", "zh-CN");
            params.put("browser_platform", "Win32");
            params.put("browser_name", "Chrome");
            params.put("browser_version", "140.0.0.0");
            params.put("browser_online", "true");
            params.put("engine_name", "Blink");
            params.put("engine_version", "140.0.0.0");
            params.put("os_name", "Windows");
            params.put("os_version", "10");
            params.put("cpu_core_num", "16");
            params.put("device_memory", "8");
            params.put("platform", "PC");
            params.put("downlink", "10");
            params.put("effective_type", "4g");
            params.put("round_trip_time", "50");
            params.put("webid", "7530992623331706407");
            params.put("uifid", uifid);

            // body: x-www-form-urlencoded
            Map<String,String> body = Map.of(
                    "aweme_id", awemeId,
                    "item_type", "0",
                    "type", String.valueOf(operationType)
            );
            String form = toForm(body);



          。。。。。。。。。。
