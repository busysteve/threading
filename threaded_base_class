#include <thread>
#include <iostream>

class threaded_base_class
{

public:
	threaded_base_class() : thd(0) 
	{ thd = new std::thread(threaded_base_class::worker, this); }

	void detach() { if(thd) thd->detach(); }
	void join()   { if(thd) thd->join();   }

	~threaded_base_class() { delete thd; }

private:
	static void worker( threaded_base_class* tp )
	{ tp->task(); }
	
	std::thread *thd;

protected:
	virtual void task()=0;
};

class MyWorker : public threaded_base_class
{
	

	void task()
	{
		while(true)
		{
			std::cout << "This is a class" << std::endl;
                	std::this_thread::sleep_for(std::chrono::milliseconds(1000));
		}
	}
};

int main( int argc, char **argv )
{
	MyWorker mw;
	mw.detach();

	while(true)
		std::this_thread::sleep_for(std::chrono::milliseconds(100));
}


