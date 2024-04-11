asset Host {
   | compromise -> buckets.delete
}

asset Account {
    | assume -> buckets.delete
}

asset Bucket {
   & delete -[1.0, 0.1]-> delete_log
   D delete_log {
        T delete
        I  self, any(account), any(host)
    }
}
