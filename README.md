# MutexExample
```
int test_recursive_mutex()
{
    std::recursive_mutex mtx;
    try
    {
        std::cout << "Start recursive_mutex example" << "!\n";
        {
            std::lock_guard<std::recursive_mutex> lock(mtx); // lock mutex
            std::cout << "First lock" << "!\n";
            {
                std::lock_guard<std::recursive_mutex> lock(mtx); // lock mutex again
                std::cout << "Second lock" << "!\n";

            }
        }
        std::cout << "Finish recursive_mutex example" << "!\n";
    }
    catch (const std::exception& ex) {
        std::cout << "Exception recursive_mutex [" << ex.what() << "]" << std::endl;
    }
    return 0;
}

int test_lock_guard()
{
    std::mutex mtx;
    try 
    {
        std::cout << "Start lock_guard example" << "!\n";
        {
            std::lock_guard<std::mutex> lock(mtx); // lock mutex
            std::cout << "First lock" << "!\n";
            {
                std::lock_guard<std::mutex> lock(mtx); // lock mutex
                std::cout << "Second lock" << "!\n";
            }
        }
        std::cout << "Finish lock_guard example" << "!\n";
    }
    catch (const std::exception& ex) {
        std::cout << "Exception lock_guard [" << ex.what() << "]" << std::endl;
    }
    return 0;
}

int main() {
    std::cout << "Mutex example\n";
    test_recursive_mutex();
    test_lock_guard();

    /*
    * Output to console:
    * Mutex example
    * Start recursive_mutex example!
    * First lock!
    * Second lock!
    * Finish recursive_mutex example!
    * Start lock_guard example!
    * First lock!
    * Exception lock_guard [device or resource busy: device or resource busy]
    */

    return 0;
}
```
