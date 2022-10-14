import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    ArrayList<String> list = new ArrayList<>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            String str = "";
            for(int i = 0; i < list.size(); i++){
                str += list.get(i) + " ";
            }
            return str;
        } else if (url.getPath().equals("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                    list.add(parameters[1]);
                    return parameters[1] + " added into the server!";
                }
            return "404 Not Found!";
        } else {
            if (url.getPath().contains("/search")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    String str = parameters[1];
                    String temp = "";
                    for(int i = 0; i < list.size(); i++){
                        if(list.get(i).contains(str)){
                            temp += list.get(i) + " ";
                        }
                    }
                    return temp;
                }
            }
            return "404 Not Found!";
        }
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
