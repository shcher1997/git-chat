# git-chat/**
 * Created by Дима on 01.11.2015.
 */
import java.io.IOException;
import java.net.*;

public class CallListener extends java.lang.Object{
    int localPort = 6868;
    String localNick;
    String remoteNick;
    String localIp;
    boolean busy;
    SocketAddress remoteAddress, listenAddress;

    CallListener(){
        ServerSocket serversocket = new ServerSocket(Connection.PORT);
    }

    public CallListener(java.lang.String localNick) {
        this.localNick=localNick;
        ServerSocket serversocket = new ServerSocket(Connection.PORT);
    }

    public CallListener(java.lang.String localNick, java.lang.String localIp) {
        this.localNick=localNick;
        this.localIp=localIp;
        ServerSocket serversocket = new ServerSocket(Connection.PORT);
    }

    public Connection getConnection() throws java.io.IOException {
        if (isBusy()) {
            return null;
        }
        else {
            ServerSocket serversocket = new ServerSocket(localPort);
            Connection connection = new Connection(serversocket.accept(), localNick);
            return connection;
        }

    }

    public java.lang.String getLocalNick() {
        return localNick;
    }

    public boolean isBusy() {
        return busy;
    }

    public java.net.SocketAddress getListenAddress() {
        return listenAddress;
    }

    public java.lang.String getRemoteNick() {
        return remoteNick;
    }


    public java.net.SocketAddress getRemoteAddress(){
        return remoteAddress;
    }

    public void setLocalNick(java.lang.String localNick) {
        this.localNick = localNick;
    }

    public void setBusy(boolean busy) {
        this.busy = busy;
    }

    public void setListenAddress(SocketAddress listenAddress) {
        this.listenAddress = listenAddress;
    }

    public static void main(java.lang.String args[]){

    }

}

